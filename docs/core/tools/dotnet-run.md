---
title: 'Uruchom polecenie: .NET Core interfejsu wiersza polecenia platformy DotNet'
description: Dotnet, uruchom polecenie zapewnia to wygodny sposób do uruchamiania aplikacji z kodu źródłowego.
author: mairaw
ms.author: mairaw
ms.date: 05/29/2018
ms.openlocfilehash: 82c6e44e52aa6af7044edf72fd6e57b7614a70f3
ms.sourcegitcommit: bbf70abe6b46073148f78cbf0619de6092b5800c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2018
ms.locfileid: "34696315"
---
# <a name="dotnet-run"></a><span data-ttu-id="9b010-103">Uruchom DotNet</span><span class="sxs-lookup"><span data-stu-id="9b010-103">dotnet run</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="9b010-104">Nazwa</span><span class="sxs-lookup"><span data-stu-id="9b010-104">Name</span></span>

<span data-ttu-id="9b010-105">`dotnet run` -Uruchamia źródła kodu bez jawnego kompilowania i uruchamiania poleceń.</span><span class="sxs-lookup"><span data-stu-id="9b010-105">`dotnet run` - Runs source code without any explicit compile or launch commands.</span></span>

## <a name="synopsis"></a><span data-ttu-id="9b010-106">Streszczenie</span><span class="sxs-lookup"><span data-stu-id="9b010-106">Synopsis</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="9b010-107">Oprogramowanie .NET core 2.1</span><span class="sxs-lookup"><span data-stu-id="9b010-107">.NET Core 2.1</span></span>](#tab/netcore21)
```
dotnet run [-c|--configuration] [-f|--framework] [--force] [--launch-profile] [--no-build] [--no-dependencies]
    [--no-launch-profile] [--no-restore] [-p|--project] [--runtime] [-v|--verbosity] [[--] [application arguments]]
dotnet run [-h|--help]
```
# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="9b010-108">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="9b010-108">.NET Core 2.0</span></span>](#tab/netcore20)
```
dotnet run [-c|--configuration] [-f|--framework] [--force] [--launch-profile] [--no-build] [--no-dependencies]
    [--no-launch-profile] [--no-restore] [-p|--project] [--runtime] [[--] [application arguments]]
dotnet run [-h|--help]
```
# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="9b010-109">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="9b010-109">.NET Core 1.x</span></span>](#tab/netcore1x)
```
dotnet run [-c|--configuration] [-f|--framework] [-p|--project] [[--] [application arguments]]
dotnet run [-h|--help]
```
---

## <a name="description"></a><span data-ttu-id="9b010-110">Opis</span><span class="sxs-lookup"><span data-stu-id="9b010-110">Description</span></span>

<span data-ttu-id="9b010-111">`dotnet run` Polecenia oferuje wygodny sposób do uruchamiania aplikacji z kodu źródłowego za pomocą jednego polecenia.</span><span class="sxs-lookup"><span data-stu-id="9b010-111">The `dotnet run` command provides a convenient option to run your application from the source code with one command.</span></span> <span data-ttu-id="9b010-112">Jest to przydatne w przypadku szybkiego iteracyjne programowanie z wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="9b010-112">It's useful for fast iterative development from the command line.</span></span> <span data-ttu-id="9b010-113">Polecenie zależy od [ `dotnet build` ](dotnet-build.md) do kompilacji kodu.</span><span class="sxs-lookup"><span data-stu-id="9b010-113">The command depends on the [`dotnet build`](dotnet-build.md) command to build the code.</span></span> <span data-ttu-id="9b010-114">Wszelkie wymagania dotyczące kompilacji, takim jak projekt musi zostać przywrócona, dotyczą `dotnet run` również.</span><span class="sxs-lookup"><span data-stu-id="9b010-114">Any requirements for the build, such as that the project must be restored first, apply to `dotnet run` as well.</span></span>

<span data-ttu-id="9b010-115">Pliki wyjściowe są zapisywane w domyślnej lokalizacji, która jest `bin/<configuration>/<target>`.</span><span class="sxs-lookup"><span data-stu-id="9b010-115">Output files are written into the default location, which is `bin/<configuration>/<target>`.</span></span> <span data-ttu-id="9b010-116">Na przykład jeśli masz `netcoreapp1.0` aplikacji i uruchom `dotnet run`, dane wyjściowe są umieszczane w `bin/Debug/netcoreapp1.0`.</span><span class="sxs-lookup"><span data-stu-id="9b010-116">For example if you have a `netcoreapp1.0` application and you run `dotnet run`, the output is placed in `bin/Debug/netcoreapp1.0`.</span></span> <span data-ttu-id="9b010-117">Pliki zostaną zastąpione, zgodnie z potrzebami.</span><span class="sxs-lookup"><span data-stu-id="9b010-117">Files are overwritten as needed.</span></span> <span data-ttu-id="9b010-118">Pliki tymczasowe są umieszczane w `obj` katalogu.</span><span class="sxs-lookup"><span data-stu-id="9b010-118">Temporary files are placed in the `obj` directory.</span></span>

<span data-ttu-id="9b010-119">Jeśli projekt określa wielu struktur, wykonywania `dotnet run` powoduje błąd, chyba że `-f|--framework <FRAMEWORK>` opcja służy do określania platformę.</span><span class="sxs-lookup"><span data-stu-id="9b010-119">If the project specifies multiple frameworks, executing `dotnet run` results in an error unless the `-f|--framework <FRAMEWORK>` option is used to specify the framework.</span></span>

<span data-ttu-id="9b010-120">`dotnet run` Polecenie jest używane w kontekście projektów nie skompilowane zestawy.</span><span class="sxs-lookup"><span data-stu-id="9b010-120">The `dotnet run` command is used in the context of projects, not built assemblies.</span></span> <span data-ttu-id="9b010-121">Jeśli zastanawiasz się do uruchomienia aplikacji zależnych od framework DLL zamiast tego należy użyć [dotnet](dotnet.md) bez polecenia.</span><span class="sxs-lookup"><span data-stu-id="9b010-121">If you're trying to run a framework-dependent application DLL instead, you must use [dotnet](dotnet.md) without a command.</span></span> <span data-ttu-id="9b010-122">Na przykład, aby uruchomić `myapp.dll`, użyj:</span><span class="sxs-lookup"><span data-stu-id="9b010-122">For example, to run `myapp.dll`, use:</span></span>

```console
dotnet myapp.dll
```

<span data-ttu-id="9b010-123">Aby uzyskać więcej informacji na temat `dotnet` sterowników, zobacz [.NET Core wiersza polecenia narzędzia (CLI)](index.md) tematu.</span><span class="sxs-lookup"><span data-stu-id="9b010-123">For more information on the `dotnet` driver, see the [.NET Core Command Line Tools (CLI)](index.md) topic.</span></span>

<span data-ttu-id="9b010-124">Aby uruchomić aplikację, `dotnet run` polecenia rozpoznaje zależności aplikacji, które znajdują się poza udostępnionym środowiska uruchomieniowego z pamięci podręcznej NuGet.</span><span class="sxs-lookup"><span data-stu-id="9b010-124">To run the application, the `dotnet run` command resolves the dependencies of the application that are outside of the shared runtime from the NuGet cache.</span></span> <span data-ttu-id="9b010-125">Ponieważ używa zależności w pamięci podręcznej, nie zalecamy używania `dotnet run` do uruchamiania aplikacji w środowisku produkcyjnym.</span><span class="sxs-lookup"><span data-stu-id="9b010-125">Because it uses cached dependencies, it's not recommended to use `dotnet run` to run applications in production.</span></span> <span data-ttu-id="9b010-126">Zamiast tego [tworzenia wdrożenia](../deploying/index.md) przy użyciu [ `dotnet publish` ](dotnet-publish.md) polecenia i wdrażanie publikowanych danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="9b010-126">Instead, [create a deployment](../deploying/index.md) using the [`dotnet publish`](dotnet-publish.md) command and deploy the published output.</span></span>

[!INCLUDE[dotnet restore note + options](~/includes/dotnet-restore-note-options.md)]

## <a name="options"></a><span data-ttu-id="9b010-127">Opcje</span><span class="sxs-lookup"><span data-stu-id="9b010-127">Options</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="9b010-128">Oprogramowanie .NET core 2.1</span><span class="sxs-lookup"><span data-stu-id="9b010-128">.NET Core 2.1</span></span>](#tab/netcore21)

`--`

<span data-ttu-id="9b010-129">Argumenty rozgranicza `dotnet run` z argumentów uruchamiania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="9b010-129">Delimits arguments to `dotnet run` from arguments for the application being run.</span></span> <span data-ttu-id="9b010-130">Wszystkie argumenty po tym ogranicznikiem są przekazywane do uruchomienia aplikacji.</span><span class="sxs-lookup"><span data-stu-id="9b010-130">All arguments after this delimiter are passed to the application run.</span></span>

`-c|--configuration {Debug|Release}`

<span data-ttu-id="9b010-131">Definiuje konfigurację kompilacji.</span><span class="sxs-lookup"><span data-stu-id="9b010-131">Defines the build configuration.</span></span> <span data-ttu-id="9b010-132">Wartość domyślna to `Debug`.</span><span class="sxs-lookup"><span data-stu-id="9b010-132">The default value is `Debug`.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="9b010-133">Tworzenie i działanie aplikacji przy użyciu określonego [framework](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="9b010-133">Builds and runs the app using the specified [framework](../../standard/frameworks.md).</span></span> <span data-ttu-id="9b010-134">Platformę należy określić w pliku projektu.</span><span class="sxs-lookup"><span data-stu-id="9b010-134">The framework must be specified in the project file.</span></span>

`--force`

<span data-ttu-id="9b010-135">Wymusza wszystkie zależności, które można rozwiązać, nawet jeśli ostatniego przywracanie zakończyło się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="9b010-135">Forces all dependencies to be resolved even if the last restore was successful.</span></span> <span data-ttu-id="9b010-136">Określenie ta flaga jest taka sama jak usuwanie *project.assets.json* pliku.</span><span class="sxs-lookup"><span data-stu-id="9b010-136">Specifying this flag is the same as deleting the *project.assets.json* file.</span></span>

`-h|--help`

<span data-ttu-id="9b010-137">Drukuje krótkich pomocy dla polecenia.</span><span class="sxs-lookup"><span data-stu-id="9b010-137">Prints out a short help for the command.</span></span>

`--launch-profile <NAME>`

<span data-ttu-id="9b010-138">Nazwa uruchomienie profilu (jeśli istnieje) do użycia podczas uruchamiania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="9b010-138">The name of the launch profile (if any) to use when launching the application.</span></span> <span data-ttu-id="9b010-139">Profile uruchamiania są zdefiniowane w *launchSettings.json* pliku i są zwykle nazywane `Development`, `Staging`, i `Production`.</span><span class="sxs-lookup"><span data-stu-id="9b010-139">Launch profiles are defined in the *launchSettings.json* file and are typically called `Development`, `Staging`, and `Production`.</span></span> <span data-ttu-id="9b010-140">Aby uzyskać więcej informacji, zobacz [Praca w środowiskach wielu](/aspnet/core/fundamentals/environments).</span><span class="sxs-lookup"><span data-stu-id="9b010-140">For more information, see [Working with multiple environments](/aspnet/core/fundamentals/environments).</span></span>

`--no-build`

<span data-ttu-id="9b010-141">Nie Skompiluj projekt przed uruchomieniem.</span><span class="sxs-lookup"><span data-stu-id="9b010-141">Doesn't build the project before running.</span></span> <span data-ttu-id="9b010-142">Niejawne także ustawia `--no-restore` flagi.</span><span class="sxs-lookup"><span data-stu-id="9b010-142">It also implicit sets the `--no-restore` flag.</span></span>

`--no-dependencies`

<span data-ttu-id="9b010-143">Podczas przywracania projektu z projektu do projektu (P2P) odwołań, przywraca i nie odwołuje się do projektu głównego.</span><span class="sxs-lookup"><span data-stu-id="9b010-143">When restoring a project with project-to-project (P2P) references, restores the root project and not the references.</span></span>

`--no-launch-profile`

<span data-ttu-id="9b010-144">Nie próbuje użyć *launchSettings.json* do skonfigurowania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="9b010-144">Doesn't try to use *launchSettings.json* to configure the application.</span></span>

`--no-restore`

<span data-ttu-id="9b010-145">Podczas uruchamiania polecenia przywracania niejawne nie jest wykonywana.</span><span class="sxs-lookup"><span data-stu-id="9b010-145">Doesn't execute an implicit restore when running the command.</span></span>

`-p|--project <PATH>`

<span data-ttu-id="9b010-146">Określa ścieżkę pliku projektu do uruchomienia (folder lub ścieżka pełna).</span><span class="sxs-lookup"><span data-stu-id="9b010-146">Specifies the path of the project file to run (folder name or full path).</span></span> <span data-ttu-id="9b010-147">Jeśli nie zostanie określony, domyślnie do bieżącego katalogu.</span><span class="sxs-lookup"><span data-stu-id="9b010-147">If not specified, it defaults to the current directory.</span></span>

`--runtime <RUNTIME_IDENTIFIER>`

<span data-ttu-id="9b010-148">Określa docelowe środowisko uruchomieniowe pod kątem przywracania pakietów dla.</span><span class="sxs-lookup"><span data-stu-id="9b010-148">Specifies the target runtime to restore packages for.</span></span> <span data-ttu-id="9b010-149">Aby uzyskać listę identyfikatorów środowiska uruchomieniowego (RID), zobacz [katalogu RID](../rid-catalog.md).</span><span class="sxs-lookup"><span data-stu-id="9b010-149">For a list of Runtime Identifiers (RIDs), see the [RID catalog](../rid-catalog.md).</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="9b010-150">Ustawia poziom szczegółowości polecenia.</span><span class="sxs-lookup"><span data-stu-id="9b010-150">Sets the verbosity level of the command.</span></span> <span data-ttu-id="9b010-151">Dozwolone wartości to `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, i `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="9b010-151">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="9b010-152">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="9b010-152">.NET Core 2.0</span></span>](#tab/netcore20)

`--`

<span data-ttu-id="9b010-153">Argumenty rozgranicza `dotnet run` z argumentów uruchamiania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="9b010-153">Delimits arguments to `dotnet run` from arguments for the application being run.</span></span> <span data-ttu-id="9b010-154">Wszystkie argumenty po tym ogranicznikiem są przekazywane do uruchomienia aplikacji.</span><span class="sxs-lookup"><span data-stu-id="9b010-154">All arguments after this delimiter are passed to the application run.</span></span>

`-c|--configuration {Debug|Release}`

<span data-ttu-id="9b010-155">Definiuje konfigurację kompilacji.</span><span class="sxs-lookup"><span data-stu-id="9b010-155">Defines the build configuration.</span></span> <span data-ttu-id="9b010-156">Wartość domyślna to `Debug`.</span><span class="sxs-lookup"><span data-stu-id="9b010-156">The default value is `Debug`.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="9b010-157">Tworzenie i działanie aplikacji przy użyciu określonego [framework](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="9b010-157">Builds and runs the app using the specified [framework](../../standard/frameworks.md).</span></span> <span data-ttu-id="9b010-158">Platformę należy określić w pliku projektu.</span><span class="sxs-lookup"><span data-stu-id="9b010-158">The framework must be specified in the project file.</span></span>

`--force`

<span data-ttu-id="9b010-159">Wymusza wszystkie zależności, które można rozwiązać, nawet jeśli ostatniego przywracanie zakończyło się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="9b010-159">Forces all dependencies to be resolved even if the last restore was successful.</span></span> <span data-ttu-id="9b010-160">Określenie ta flaga jest taka sama jak usuwanie *project.assets.json* pliku.</span><span class="sxs-lookup"><span data-stu-id="9b010-160">Specifying this flag is the same as deleting the *project.assets.json* file.</span></span>

`-h|--help`

<span data-ttu-id="9b010-161">Drukuje krótkich pomocy dla polecenia.</span><span class="sxs-lookup"><span data-stu-id="9b010-161">Prints out a short help for the command.</span></span>

`--launch-profile <NAME>`

<span data-ttu-id="9b010-162">Nazwa uruchomienie profilu (jeśli istnieje) do użycia podczas uruchamiania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="9b010-162">The name of the launch profile (if any) to use when launching the application.</span></span> <span data-ttu-id="9b010-163">Profile uruchamiania są zdefiniowane w *launchSettings.json* pliku i są zwykle nazywane `Development`, `Staging`, i `Production`.</span><span class="sxs-lookup"><span data-stu-id="9b010-163">Launch profiles are defined in the *launchSettings.json* file and are typically called `Development`, `Staging`, and `Production`.</span></span> <span data-ttu-id="9b010-164">Aby uzyskać więcej informacji, zobacz [Praca w środowiskach wielu](/aspnet/core/fundamentals/environments).</span><span class="sxs-lookup"><span data-stu-id="9b010-164">For more information, see [Working with multiple environments](/aspnet/core/fundamentals/environments).</span></span>

`--no-build`

<span data-ttu-id="9b010-165">Nie Skompiluj projekt przed uruchomieniem.</span><span class="sxs-lookup"><span data-stu-id="9b010-165">Doesn't build the project before running.</span></span> <span data-ttu-id="9b010-166">Niejawne także ustawia `--no-restore` flagi.</span><span class="sxs-lookup"><span data-stu-id="9b010-166">It also implicit sets the `--no-restore` flag.</span></span>

`--no-dependencies`

<span data-ttu-id="9b010-167">Podczas przywracania projektu z projektu do projektu (P2P) odwołań, przywraca i nie odwołuje się do projektu głównego.</span><span class="sxs-lookup"><span data-stu-id="9b010-167">When restoring a project with project-to-project (P2P) references, restores the root project and not the references.</span></span>

`--no-launch-profile`

<span data-ttu-id="9b010-168">Nie próbuje użyć *launchSettings.json* do skonfigurowania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="9b010-168">Doesn't try to use *launchSettings.json* to configure the application.</span></span>

`--no-restore`

<span data-ttu-id="9b010-169">Podczas uruchamiania polecenia przywracania niejawne nie jest wykonywana.</span><span class="sxs-lookup"><span data-stu-id="9b010-169">Doesn't execute an implicit restore when running the command.</span></span>

`-p|--project <PATH>`

<span data-ttu-id="9b010-170">Określa ścieżkę pliku projektu do uruchomienia (folder lub ścieżka pełna).</span><span class="sxs-lookup"><span data-stu-id="9b010-170">Specifies the path of the project file to run (folder name or full path).</span></span> <span data-ttu-id="9b010-171">Jeśli nie zostanie określony, domyślnie do bieżącego katalogu.</span><span class="sxs-lookup"><span data-stu-id="9b010-171">If not specified, it defaults to the current directory.</span></span>

`--runtime <RUNTIME_IDENTIFIER>`

<span data-ttu-id="9b010-172">Określa docelowe środowisko uruchomieniowe pod kątem przywracania pakietów dla.</span><span class="sxs-lookup"><span data-stu-id="9b010-172">Specifies the target runtime to restore packages for.</span></span> <span data-ttu-id="9b010-173">Aby uzyskać listę identyfikatorów środowiska uruchomieniowego (RID), zobacz [katalogu RID](../rid-catalog.md).</span><span class="sxs-lookup"><span data-stu-id="9b010-173">For a list of Runtime Identifiers (RIDs), see the [RID catalog](../rid-catalog.md).</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="9b010-174">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="9b010-174">.NET Core 1.x</span></span>](#tab/netcore1x)

`--`

<span data-ttu-id="9b010-175">Argumenty rozgranicza `dotnet run` z argumentów uruchamiania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="9b010-175">Delimits arguments to `dotnet run` from arguments for the application being run.</span></span> <span data-ttu-id="9b010-176">Wszystkie argumenty po tym ogranicznikiem są przekazywane do uruchomienia aplikacji.</span><span class="sxs-lookup"><span data-stu-id="9b010-176">All arguments after this delimiter are passed to the application run.</span></span>

`-c|--configuration {Debug|Release}`

<span data-ttu-id="9b010-177">Definiuje konfigurację kompilacji.</span><span class="sxs-lookup"><span data-stu-id="9b010-177">Defines the build configuration.</span></span> <span data-ttu-id="9b010-178">Wartość domyślna to `Debug`.</span><span class="sxs-lookup"><span data-stu-id="9b010-178">The default value is `Debug`.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="9b010-179">Tworzenie i działanie aplikacji przy użyciu określonego [framework](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="9b010-179">Builds and runs the app using the specified [framework](../../standard/frameworks.md).</span></span> <span data-ttu-id="9b010-180">Platformę należy określić w pliku projektu.</span><span class="sxs-lookup"><span data-stu-id="9b010-180">The framework must be specified in the project file.</span></span>

`-h|--help`

<span data-ttu-id="9b010-181">Drukuje krótkich pomocy dla polecenia.</span><span class="sxs-lookup"><span data-stu-id="9b010-181">Prints out a short help for the command.</span></span>

`-p|--project <PATH/PROJECT.csproj>`

<span data-ttu-id="9b010-182">Określa ścieżkę i nazwę pliku projektu.</span><span class="sxs-lookup"><span data-stu-id="9b010-182">Specifies the path and name of the project file.</span></span> <span data-ttu-id="9b010-183">(Patrz Notatka). Jeśli nie zostanie określony, domyślnie do bieżącego katalogu.</span><span class="sxs-lookup"><span data-stu-id="9b010-183">(See the NOTE.) If not specified, it defaults to the current directory.</span></span>

> [!NOTE]
> <span data-ttu-id="9b010-184">Użyj ścieżka i nazwa pliku projektu z `-p|--project` opcji.</span><span class="sxs-lookup"><span data-stu-id="9b010-184">Use the path and name of the project file with the `-p|--project` option.</span></span> <span data-ttu-id="9b010-185">Regresja w interfejsu wiersza polecenia uniemożliwia dostarczanie ścieżkę folderu zestawu SDK programu .NET Core 1.x.</span><span class="sxs-lookup"><span data-stu-id="9b010-185">A regression in the CLI prevents providing a folder path with .NET Core SDK 1.x.</span></span> <span data-ttu-id="9b010-186">Aby uzyskać więcej informacji na temat tego problemu, zobacz [dotnet Uruchom -p, nie można uruchomić projektu (dotnet/cli #5992)](https://github.com/dotnet/cli/issues/5992).</span><span class="sxs-lookup"><span data-stu-id="9b010-186">For more information about this issue, see [dotnet run -p, can not start a project (dotnet/cli #5992)](https://github.com/dotnet/cli/issues/5992).</span></span>

---

## <a name="examples"></a><span data-ttu-id="9b010-187">Przykłady</span><span class="sxs-lookup"><span data-stu-id="9b010-187">Examples</span></span>

<span data-ttu-id="9b010-188">Uruchom projekt w bieżącym katalogu:</span><span class="sxs-lookup"><span data-stu-id="9b010-188">Run the project in the current directory:</span></span>

`dotnet run`

<span data-ttu-id="9b010-189">Uruchamia określony projekt:</span><span class="sxs-lookup"><span data-stu-id="9b010-189">Run the specified project:</span></span>

`dotnet run --project /projects/proj1/proj1.csproj`

<span data-ttu-id="9b010-190">Uruchom projekt w bieżącym katalogu ( `--help` argument w tym przykładzie jest przekazywany do aplikacji, ponieważ `--` argument jest używany):</span><span class="sxs-lookup"><span data-stu-id="9b010-190">Run the project in the current directory (the `--help` argument in this example is passed to the application, since the `--` argument is used):</span></span>

`dotnet run --configuration Release -- --help`

<span data-ttu-id="9b010-191">Przywróć zależności i narzędzi dla projektu w bieżącym katalogu tylko przedstawiający minimalnego danych wyjściowych, a następnie uruchom projekt: (.NET Core SDK 2.0 i nowsze wersje):</span><span class="sxs-lookup"><span data-stu-id="9b010-191">Restore dependencies and tools for the project in the current directory only showing minimal output and then run the project: (.NET Core SDK 2.0 and later versions):</span></span>

`dotnet run --verbosity m`