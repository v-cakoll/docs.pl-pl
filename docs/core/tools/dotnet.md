---
title: dotnet — polecenie
description: Dowiedz się więcej na temat polecenia dotnet (sterownika generycznego dla narzędzi interfejs wiersza polecenia platformy .NET Core) i jego użycia.
ms.date: 06/04/2018
ms.openlocfilehash: 7e1915610732151487353f2d14586597f801ddfb
ms.sourcegitcommit: 1b020356e421a9314dd525539da12463d980ce7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/30/2019
ms.locfileid: "70167919"
---
# <a name="dotnet-command"></a><span data-ttu-id="afe44-103">dotnet — polecenie</span><span class="sxs-lookup"><span data-stu-id="afe44-103">dotnet command</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="afe44-104">Nazwa</span><span class="sxs-lookup"><span data-stu-id="afe44-104">Name</span></span>

<span data-ttu-id="afe44-105">`dotnet`-Narzędzie do zarządzania kodem źródłowym i plikami binarnymi platformy .NET.</span><span class="sxs-lookup"><span data-stu-id="afe44-105">`dotnet` - A tool for managing .NET source code and binaries.</span></span>

## <a name="synopsis"></a><span data-ttu-id="afe44-106">Streszczenie</span><span class="sxs-lookup"><span data-stu-id="afe44-106">Synopsis</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="afe44-107">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="afe44-107">.NET Core 2.1</span></span>](#tab/netcore21)

```console
dotnet [command] [arguments] [--additional-deps] [--additionalprobingpath] [-d|--diagnostics] [--fx-version]
    [-h|--help] [--info] [--list-runtimes] [--list-sdks] [--roll-forward-on-no-candidate-fx] [-v|--verbosity] [--version]
```

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="afe44-108">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="afe44-108">.NET Core 2.0</span></span>](#tab/netcore20)

```console
dotnet [command] [arguments] [--additional-deps] [--additionalprobingpath] [-d|--diagnostics]
    [--fx-version] [-h|--help] [--info] [--roll-forward-on-no-candidate-fx] [-v|--verbosity] [--version]
```

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="afe44-109">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="afe44-109">.NET Core 1.x</span></span>](#tab/netcore1x)

```console
dotnet [command] [arguments] [--additionalprobingpath] [-d|--diagnostics] [--fx-version]
    [-h|--help] [--info] [-v|--verbosity] [--version]
```

---

## <a name="description"></a><span data-ttu-id="afe44-110">Opis</span><span class="sxs-lookup"><span data-stu-id="afe44-110">Description</span></span>

<span data-ttu-id="afe44-111">`dotnet`jest narzędziem do zarządzania kodem źródłowym i plikami binarnymi platformy .NET.</span><span class="sxs-lookup"><span data-stu-id="afe44-111">`dotnet` is a tool for managing .NET source code and binaries.</span></span> <span data-ttu-id="afe44-112">Udostępnia polecenia wykonujące określone zadania, takie jak [`dotnet build`](dotnet-build.md) i. [`dotnet run`](dotnet-run.md)</span><span class="sxs-lookup"><span data-stu-id="afe44-112">It exposes commands that perform specific tasks, such as [`dotnet build`](dotnet-build.md) and [`dotnet run`](dotnet-run.md).</span></span> <span data-ttu-id="afe44-113">Każde polecenie definiuje własne argumenty.</span><span class="sxs-lookup"><span data-stu-id="afe44-113">Each command defines its own arguments.</span></span> <span data-ttu-id="afe44-114">Wpisz `--help` po każdym poleceniu, aby uzyskać dostęp do krótkiej dokumentacji pomocy.</span><span class="sxs-lookup"><span data-stu-id="afe44-114">Type `--help` after each command to access brief help documentation.</span></span>

<span data-ttu-id="afe44-115">`dotnet`może służyć do uruchamiania aplikacji przez określenie biblioteki DLL aplikacji, takiej jak `dotnet myapp.dll`.</span><span class="sxs-lookup"><span data-stu-id="afe44-115">`dotnet` can be used to run applications, by specifying an application DLL, such as `dotnet myapp.dll`.</span></span> <span data-ttu-id="afe44-116">Zobacz [wdrażanie aplikacji .NET Core](../deploying/index.md) w celu uzyskania informacji na temat opcji wdrażania.</span><span class="sxs-lookup"><span data-stu-id="afe44-116">See [.NET Core application deployment](../deploying/index.md) for to learn about deployment options.</span></span>

## <a name="options"></a><span data-ttu-id="afe44-117">Opcje</span><span class="sxs-lookup"><span data-stu-id="afe44-117">Options</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="afe44-118">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="afe44-118">.NET Core 2.1</span></span>](#tab/netcore21)

`--additional-deps <PATH>`

<span data-ttu-id="afe44-119">Ścieżka do pliku dodatkowego *. deps. JSON* .</span><span class="sxs-lookup"><span data-stu-id="afe44-119">Path to additional *.deps.json* file.</span></span>

`--additionalprobingpath <PATH>`

<span data-ttu-id="afe44-120">Ścieżka zawierająca zasady i zestawy do sondowania.</span><span class="sxs-lookup"><span data-stu-id="afe44-120">Path containing probing policy and assemblies to probe.</span></span>

`-d|--diagnostics`

<span data-ttu-id="afe44-121">Włącza diagnostykę danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="afe44-121">Enables diagnostic output.</span></span>

`--fx-version <VERSION>`

<span data-ttu-id="afe44-122">Wersja środowiska uruchomieniowego platformy .NET Core do użycia w celu uruchomienia aplikacji.</span><span class="sxs-lookup"><span data-stu-id="afe44-122">Version of the .NET Core runtime to use to run the application.</span></span>

`-h|--help`

<span data-ttu-id="afe44-123">Drukuje dokumentację dla danego polecenia, na przykład `dotnet build --help`.</span><span class="sxs-lookup"><span data-stu-id="afe44-123">Prints out documentation for a given command, such as `dotnet build --help`.</span></span> <span data-ttu-id="afe44-124">`dotnet --help`Drukuje listę dostępnych poleceń.</span><span class="sxs-lookup"><span data-stu-id="afe44-124">`dotnet --help` prints a list of available commands.</span></span>

`--info`

<span data-ttu-id="afe44-125">Drukuje szczegółowe informacje na temat instalacji programu .NET Core i środowiska maszynowego, takiego jak bieżący system operacyjny, i zatwierdzania SHA dla wersji .NET Core.</span><span class="sxs-lookup"><span data-stu-id="afe44-125">Prints out detailed information about a .NET Core installation and the machine environment, such as the current operating system, and commit SHA of the .NET Core version.</span></span>

`--list-runtimes`

<span data-ttu-id="afe44-126">Wyświetla zainstalowane środowiska uruchomieniowe platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="afe44-126">Displays the installed .NET Core runtimes.</span></span>

`--list-sdks`

<span data-ttu-id="afe44-127">Wyświetla zainstalowane zestawy SDK platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="afe44-127">Displays the installed .NET Core SDKs.</span></span>

`--roll-forward-on-no-candidate-fx <N>`

<span data-ttu-id="afe44-128">Definiuje zachowanie, gdy wymagana architektura udostępniona jest niedostępna.</span><span class="sxs-lookup"><span data-stu-id="afe44-128">Defines behavior when the required shared framework is not available.</span></span> <span data-ttu-id="afe44-129">`N` może być:</span><span class="sxs-lookup"><span data-stu-id="afe44-129">`N` can be:</span></span>
* <span data-ttu-id="afe44-130">`0`-Wyłącz parzystą wersję pomocniczą do przodu.</span><span class="sxs-lookup"><span data-stu-id="afe44-130">`0` - Disable even minor version roll forward.</span></span>
* <span data-ttu-id="afe44-131">`1`— Przewinięcie do wersji pomocniczej, ale nie w wersji głównej.</span><span class="sxs-lookup"><span data-stu-id="afe44-131">`1` - Roll forward on minor version, but not on major version.</span></span> <span data-ttu-id="afe44-132">Jest to zachowanie domyślne.</span><span class="sxs-lookup"><span data-stu-id="afe44-132">This is the default behavior.</span></span>
* <span data-ttu-id="afe44-133">`2`— Przewinięcie do przodu w wersjach pomocniczych i głównych.</span><span class="sxs-lookup"><span data-stu-id="afe44-133">`2` - Roll forward on minor and major versions.</span></span>

 <span data-ttu-id="afe44-134">Aby uzyskać więcej informacji, zobacz [przewinięcie do przodu](../whats-new/dotnet-core-2-1.md#roll-forward).</span><span class="sxs-lookup"><span data-stu-id="afe44-134">For more information, see [Roll forward](../whats-new/dotnet-core-2-1.md#roll-forward).</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="afe44-135">Ustawia poziom szczegółowości polecenia.</span><span class="sxs-lookup"><span data-stu-id="afe44-135">Sets the verbosity level of the command.</span></span> <span data-ttu-id="afe44-136">Dozwolone wartości to `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`i .`diag[nostic]`</span><span class="sxs-lookup"><span data-stu-id="afe44-136">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="afe44-137">Nieobsługiwane w każdym poleceniu; Aby określić, czy ta opcja jest dostępna, zobacz określoną stronę poleceń.</span><span class="sxs-lookup"><span data-stu-id="afe44-137">Not supported in every command; see specific command page to determine if this option is available.</span></span>

`--version`

<span data-ttu-id="afe44-138">Drukuje używaną wersję zestaw .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="afe44-138">Prints out the version of the .NET Core SDK in use.</span></span>

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="afe44-139">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="afe44-139">.NET Core 2.0</span></span>](#tab/netcore20)

`--additional-deps <PATH>`

<span data-ttu-id="afe44-140">Ścieżka do pliku dodatkowego *. deps. JSON* .</span><span class="sxs-lookup"><span data-stu-id="afe44-140">Path to additional *.deps.json* file.</span></span>

`--additionalprobingpath <PATH>`

<span data-ttu-id="afe44-141">Ścieżka zawierająca zasady i zestawy do sondowania.</span><span class="sxs-lookup"><span data-stu-id="afe44-141">Path containing probing policy and assemblies to probe.</span></span>

`-d|--diagnostics`

<span data-ttu-id="afe44-142">Włącza diagnostykę danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="afe44-142">Enables diagnostic output.</span></span>

`--fx-version <VERSION>`

<span data-ttu-id="afe44-143">Wersja środowiska uruchomieniowego platformy .NET Core do użycia w celu uruchomienia aplikacji.</span><span class="sxs-lookup"><span data-stu-id="afe44-143">Version of the .NET Core runtime to use to run the application.</span></span>

`-h|--help`

<span data-ttu-id="afe44-144">Drukuje dokumentację dla danego polecenia, na przykład `dotnet build --help`.</span><span class="sxs-lookup"><span data-stu-id="afe44-144">Prints out documentation for a given command, such as `dotnet build --help`.</span></span> <span data-ttu-id="afe44-145">`dotnet --help`Drukuje listę dostępnych poleceń.</span><span class="sxs-lookup"><span data-stu-id="afe44-145">`dotnet --help` prints a list of available commands.</span></span>

`--info`

<span data-ttu-id="afe44-146">Drukuje szczegółowe informacje na temat instalacji programu .NET Core i środowiska maszynowego, takiego jak bieżący system operacyjny, i zatwierdzania SHA dla wersji .NET Core.</span><span class="sxs-lookup"><span data-stu-id="afe44-146">Prints out detailed information about a .NET Core installation and the machine environment, such as the current operating system, and commit SHA of the .NET Core version.</span></span>

`--roll-forward-on-no-candidate-fx`

 <span data-ttu-id="afe44-147">Wyłącza dodatkową wersję do przodu, jeśli jest ustawiona `0`na.</span><span class="sxs-lookup"><span data-stu-id="afe44-147">Disables minor version roll forward, if set to `0`.</span></span> <span data-ttu-id="afe44-148">Aby uzyskać więcej informacji, zobacz [przewinięcie do przodu](../whats-new/dotnet-core-2-1.md#roll-forward).</span><span class="sxs-lookup"><span data-stu-id="afe44-148">For more information, see [Roll forward](../whats-new/dotnet-core-2-1.md#roll-forward).</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="afe44-149">Ustawia poziom szczegółowości polecenia.</span><span class="sxs-lookup"><span data-stu-id="afe44-149">Sets the verbosity level of the command.</span></span> <span data-ttu-id="afe44-150">Dozwolone wartości to `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`i .`diag[nostic]`</span><span class="sxs-lookup"><span data-stu-id="afe44-150">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="afe44-151">Nieobsługiwane w każdym poleceniu; Aby określić, czy ta opcja jest dostępna, zobacz określoną stronę poleceń.</span><span class="sxs-lookup"><span data-stu-id="afe44-151">Not supported in every command; see specific command page to determine if this option is available.</span></span>

`--version`

<span data-ttu-id="afe44-152">Drukuje używaną wersję zestaw .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="afe44-152">Prints out the version of the .NET Core SDK in use.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="afe44-153">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="afe44-153">.NET Core 1.x</span></span>](#tab/netcore1x)

`--additionalprobingpath <PATH>`

<span data-ttu-id="afe44-154">Ścieżka zawierająca zasady i zestawy do sondowania.</span><span class="sxs-lookup"><span data-stu-id="afe44-154">Path containing probing policy and assemblies to probe.</span></span>

`-d|--diagnostics`

<span data-ttu-id="afe44-155">Włącza diagnostykę danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="afe44-155">Enables diagnostic output.</span></span>

`--fx-version <VERSION>`

<span data-ttu-id="afe44-156">Wersja środowiska uruchomieniowego platformy .NET Core do użycia w celu uruchomienia aplikacji.</span><span class="sxs-lookup"><span data-stu-id="afe44-156">Version of the .NET Core runtime to use to run the application.</span></span>

`-h|--help`

<span data-ttu-id="afe44-157">Drukuje dokumentację dla danego polecenia, na przykład `dotnet build --help`.</span><span class="sxs-lookup"><span data-stu-id="afe44-157">Prints out documentation for a given command, such as `dotnet build --help`.</span></span> <span data-ttu-id="afe44-158">`dotnet --help`Drukuje listę dostępnych poleceń.</span><span class="sxs-lookup"><span data-stu-id="afe44-158">`dotnet --help` prints a list of available commands.</span></span>

`--info`

<span data-ttu-id="afe44-159">Drukuje szczegółowe informacje na temat instalacji programu .NET Core i środowiska maszynowego, takiego jak bieżący system operacyjny, i zatwierdzania SHA dla wersji .NET Core.</span><span class="sxs-lookup"><span data-stu-id="afe44-159">Prints out detailed information about a .NET Core installation and the machine environment, such as the current operating system, and commit SHA of the .NET Core version.</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="afe44-160">Ustawia poziom szczegółowości polecenia.</span><span class="sxs-lookup"><span data-stu-id="afe44-160">Sets the verbosity level of the command.</span></span> <span data-ttu-id="afe44-161">Dozwolone wartości to `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`i .`diag[nostic]`</span><span class="sxs-lookup"><span data-stu-id="afe44-161">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="afe44-162">Nieobsługiwane w każdym poleceniu; Aby określić, czy ta opcja jest dostępna, zobacz określoną stronę poleceń.</span><span class="sxs-lookup"><span data-stu-id="afe44-162">Not supported in every command; see specific command page to determine if this option is available.</span></span>

`--version`

<span data-ttu-id="afe44-163">Drukuje używaną wersję zestaw .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="afe44-163">Prints out the version of the .NET Core SDK in use.</span></span>

---

## <a name="dotnet-commands"></a><span data-ttu-id="afe44-164">Polecenia dotnet</span><span class="sxs-lookup"><span data-stu-id="afe44-164">dotnet commands</span></span>

### <a name="general"></a><span data-ttu-id="afe44-165">Ogólne</span><span class="sxs-lookup"><span data-stu-id="afe44-165">General</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="afe44-166">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="afe44-166">.NET Core 2.1</span></span>](#tab/netcore21)

| <span data-ttu-id="afe44-167">Polecenie</span><span class="sxs-lookup"><span data-stu-id="afe44-167">Command</span></span>                                       | <span data-ttu-id="afe44-168">Funkcja</span><span class="sxs-lookup"><span data-stu-id="afe44-168">Function</span></span>                                                            |
| --------------------------------------------- | ------------------------------------------------------------------- |
| [<span data-ttu-id="afe44-169">dotnet build</span><span class="sxs-lookup"><span data-stu-id="afe44-169">dotnet build</span></span>](dotnet-build.md)               | <span data-ttu-id="afe44-170">Kompiluje aplikację platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="afe44-170">Builds a .NET Core application.</span></span>                                     |
| [<span data-ttu-id="afe44-171">dotnet build-server</span><span class="sxs-lookup"><span data-stu-id="afe44-171">dotnet build-server</span></span>](dotnet-build-server.md) | <span data-ttu-id="afe44-172">Współdziała z serwerami uruchomionymi przez kompilację.</span><span class="sxs-lookup"><span data-stu-id="afe44-172">Interacts with servers started by a build.</span></span>                          |
| [<span data-ttu-id="afe44-173">dotnet clean</span><span class="sxs-lookup"><span data-stu-id="afe44-173">dotnet clean</span></span>](dotnet-clean.md)               | <span data-ttu-id="afe44-174">Czyste dane wyjściowe kompilacji.</span><span class="sxs-lookup"><span data-stu-id="afe44-174">Clean build outputs.</span></span>                                                |
| [<span data-ttu-id="afe44-175">dotnet help</span><span class="sxs-lookup"><span data-stu-id="afe44-175">dotnet help</span></span>](dotnet-help.md)                 | <span data-ttu-id="afe44-176">Przedstawia bardziej szczegółową dokumentację dla polecenia w trybie online.</span><span class="sxs-lookup"><span data-stu-id="afe44-176">Shows more detailed documentation online for the command.</span></span>           |
| [<span data-ttu-id="afe44-177">dotnet migrate</span><span class="sxs-lookup"><span data-stu-id="afe44-177">dotnet migrate</span></span>](dotnet-migrate.md)           | <span data-ttu-id="afe44-178">Migruje prawidłowy projekt w wersji zapoznawczej 2 do projektu zestaw .NET Core SDK 1,0.</span><span class="sxs-lookup"><span data-stu-id="afe44-178">Migrates a valid Preview 2 project to a .NET Core SDK 1.0 project.</span></span>  |
| [<span data-ttu-id="afe44-179">dotnet msbuild</span><span class="sxs-lookup"><span data-stu-id="afe44-179">dotnet msbuild</span></span>](dotnet-msbuild.md)           | <span data-ttu-id="afe44-180">Zapewnia dostęp do wiersza polecenia programu MSBuild.</span><span class="sxs-lookup"><span data-stu-id="afe44-180">Provides access to the MSBuild command line.</span></span>                        |
| [<span data-ttu-id="afe44-181">dotnet new</span><span class="sxs-lookup"><span data-stu-id="afe44-181">dotnet new</span></span>](dotnet-new.md)                   | <span data-ttu-id="afe44-182">Inicjuje projekt C# lub F# dla danego szablonu.</span><span class="sxs-lookup"><span data-stu-id="afe44-182">Initializes a C# or F# project for a given template.</span></span>                |
| [<span data-ttu-id="afe44-183">dotnet pack</span><span class="sxs-lookup"><span data-stu-id="afe44-183">dotnet pack</span></span>](dotnet-pack.md)                 | <span data-ttu-id="afe44-184">Tworzy pakiet NuGet kodu.</span><span class="sxs-lookup"><span data-stu-id="afe44-184">Creates a NuGet package of your code.</span></span>                               |
| [<span data-ttu-id="afe44-185">dotnet publish</span><span class="sxs-lookup"><span data-stu-id="afe44-185">dotnet publish</span></span>](dotnet-publish.md)           | <span data-ttu-id="afe44-186">Publikuje zależne od programu .NET Framework lub samodzielną aplikację.</span><span class="sxs-lookup"><span data-stu-id="afe44-186">Publishes a .NET framework-dependent or self-contained application.</span></span> |
| [<span data-ttu-id="afe44-187">dotnet restore</span><span class="sxs-lookup"><span data-stu-id="afe44-187">dotnet restore</span></span>](dotnet-restore.md)           | <span data-ttu-id="afe44-188">Przywraca zależności dla danej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="afe44-188">Restores the dependencies for a given application.</span></span>                  |
| [<span data-ttu-id="afe44-189">dotnet run</span><span class="sxs-lookup"><span data-stu-id="afe44-189">dotnet run</span></span>](dotnet-run.md)                   | <span data-ttu-id="afe44-190">Uruchamia aplikację ze źródła.</span><span class="sxs-lookup"><span data-stu-id="afe44-190">Runs the application from source.</span></span>                                   |
| [<span data-ttu-id="afe44-191">dotnet sln</span><span class="sxs-lookup"><span data-stu-id="afe44-191">dotnet sln</span></span>](dotnet-sln.md)                   | <span data-ttu-id="afe44-192">Opcje dodawania, usuwania i wyświetlania listy projektów w pliku rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="afe44-192">Options to add, remove, and list projects in a solution file.</span></span>       |
| [<span data-ttu-id="afe44-193">dotnet store</span><span class="sxs-lookup"><span data-stu-id="afe44-193">dotnet store</span></span>](dotnet-store.md)               | <span data-ttu-id="afe44-194">Przechowuje zestawy w magazynie pakietów środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="afe44-194">Stores assemblies in the runtime package store.</span></span>                     |
| [<span data-ttu-id="afe44-195">dotnet test</span><span class="sxs-lookup"><span data-stu-id="afe44-195">dotnet test</span></span>](dotnet-test.md)                 | <span data-ttu-id="afe44-196">Uruchamia testy przy użyciu modułu uruchamiającego testy.</span><span class="sxs-lookup"><span data-stu-id="afe44-196">Runs tests using a test runner.</span></span>                                     |

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="afe44-197">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="afe44-197">.NET Core 2.0</span></span>](#tab/netcore20)

| <span data-ttu-id="afe44-198">Polecenie</span><span class="sxs-lookup"><span data-stu-id="afe44-198">Command</span></span>                             | <span data-ttu-id="afe44-199">Funkcja</span><span class="sxs-lookup"><span data-stu-id="afe44-199">Function</span></span>                                                            |
| ----------------------------------- | ------------------------------------------------------------------- |
| [<span data-ttu-id="afe44-200">dotnet build</span><span class="sxs-lookup"><span data-stu-id="afe44-200">dotnet build</span></span>](dotnet-build.md)     | <span data-ttu-id="afe44-201">Kompiluje aplikację platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="afe44-201">Builds a .NET Core application.</span></span>                                     |
| [<span data-ttu-id="afe44-202">dotnet clean</span><span class="sxs-lookup"><span data-stu-id="afe44-202">dotnet clean</span></span>](dotnet-clean.md)     | <span data-ttu-id="afe44-203">Czyste dane wyjściowe kompilacji.</span><span class="sxs-lookup"><span data-stu-id="afe44-203">Clean build outputs.</span></span>                                              |
| [<span data-ttu-id="afe44-204">dotnet help</span><span class="sxs-lookup"><span data-stu-id="afe44-204">dotnet help</span></span>](dotnet-help.md)       | <span data-ttu-id="afe44-205">Przedstawia bardziej szczegółową dokumentację dla polecenia w trybie online.</span><span class="sxs-lookup"><span data-stu-id="afe44-205">Shows more detailed documentation online for the command.</span></span>           |
| [<span data-ttu-id="afe44-206">dotnet migrate</span><span class="sxs-lookup"><span data-stu-id="afe44-206">dotnet migrate</span></span>](dotnet-migrate.md) | <span data-ttu-id="afe44-207">Migruje prawidłowy projekt w wersji zapoznawczej 2 do projektu zestaw .NET Core SDK 1,0.</span><span class="sxs-lookup"><span data-stu-id="afe44-207">Migrates a valid Preview 2 project to a .NET Core SDK 1.0 project.</span></span>  |
| [<span data-ttu-id="afe44-208">dotnet msbuild</span><span class="sxs-lookup"><span data-stu-id="afe44-208">dotnet msbuild</span></span>](dotnet-msbuild.md) | <span data-ttu-id="afe44-209">Zapewnia dostęp do wiersza polecenia programu MSBuild.</span><span class="sxs-lookup"><span data-stu-id="afe44-209">Provides access to the MSBuild command line.</span></span>                        |
| [<span data-ttu-id="afe44-210">dotnet new</span><span class="sxs-lookup"><span data-stu-id="afe44-210">dotnet new</span></span>](dotnet-new.md)         | <span data-ttu-id="afe44-211">Inicjuje projekt C# lub F# dla danego szablonu.</span><span class="sxs-lookup"><span data-stu-id="afe44-211">Initializes a C# or F# project for a given template.</span></span>                |
| [<span data-ttu-id="afe44-212">dotnet pack</span><span class="sxs-lookup"><span data-stu-id="afe44-212">dotnet pack</span></span>](dotnet-pack.md)       | <span data-ttu-id="afe44-213">Tworzy pakiet NuGet kodu.</span><span class="sxs-lookup"><span data-stu-id="afe44-213">Creates a NuGet package of your code.</span></span>                               |
| [<span data-ttu-id="afe44-214">dotnet publish</span><span class="sxs-lookup"><span data-stu-id="afe44-214">dotnet publish</span></span>](dotnet-publish.md) | <span data-ttu-id="afe44-215">Publikuje zależne od programu .NET Framework lub samodzielną aplikację.</span><span class="sxs-lookup"><span data-stu-id="afe44-215">Publishes a .NET framework-dependent or self-contained application.</span></span> |
| [<span data-ttu-id="afe44-216">dotnet restore</span><span class="sxs-lookup"><span data-stu-id="afe44-216">dotnet restore</span></span>](dotnet-restore.md) | <span data-ttu-id="afe44-217">Przywraca zależności dla danej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="afe44-217">Restores the dependencies for a given application.</span></span>                  |
| [<span data-ttu-id="afe44-218">dotnet run</span><span class="sxs-lookup"><span data-stu-id="afe44-218">dotnet run</span></span>](dotnet-run.md)         | <span data-ttu-id="afe44-219">Uruchamia aplikację ze źródła.</span><span class="sxs-lookup"><span data-stu-id="afe44-219">Runs the application from source.</span></span>                                   |
| [<span data-ttu-id="afe44-220">dotnet sln</span><span class="sxs-lookup"><span data-stu-id="afe44-220">dotnet sln</span></span>](dotnet-sln.md)         | <span data-ttu-id="afe44-221">Opcje dodawania, usuwania i wyświetlania listy projektów w pliku rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="afe44-221">Options to add, remove, and list projects in a solution file.</span></span>       |
| [<span data-ttu-id="afe44-222">dotnet store</span><span class="sxs-lookup"><span data-stu-id="afe44-222">dotnet store</span></span>](dotnet-store.md)     | <span data-ttu-id="afe44-223">Przechowuje zestawy w magazynie pakietów środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="afe44-223">Stores assemblies in the runtime package store.</span></span>                     |
| [<span data-ttu-id="afe44-224">dotnet test</span><span class="sxs-lookup"><span data-stu-id="afe44-224">dotnet test</span></span>](dotnet-test.md)       | <span data-ttu-id="afe44-225">Uruchamia testy przy użyciu modułu uruchamiającego testy.</span><span class="sxs-lookup"><span data-stu-id="afe44-225">Runs tests using a test runner.</span></span>                                     |

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="afe44-226">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="afe44-226">.NET Core 1.x</span></span>](#tab/netcore1x)

| <span data-ttu-id="afe44-227">Polecenie</span><span class="sxs-lookup"><span data-stu-id="afe44-227">Command</span></span>                             | <span data-ttu-id="afe44-228">Funkcja</span><span class="sxs-lookup"><span data-stu-id="afe44-228">Function</span></span>                                                            |
| ----------------------------------- | ------------------------------------------------------------------- |
| [<span data-ttu-id="afe44-229">dotnet build</span><span class="sxs-lookup"><span data-stu-id="afe44-229">dotnet build</span></span>](dotnet-build.md)     | <span data-ttu-id="afe44-230">Kompiluje aplikację platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="afe44-230">Builds a .NET Core application.</span></span>                                     |
| [<span data-ttu-id="afe44-231">dotnet clean</span><span class="sxs-lookup"><span data-stu-id="afe44-231">dotnet clean</span></span>](dotnet-clean.md)     | <span data-ttu-id="afe44-232">Czyste dane wyjściowe kompilacji.</span><span class="sxs-lookup"><span data-stu-id="afe44-232">Clean build outputs.</span></span>                                              |
| [<span data-ttu-id="afe44-233">dotnet migrate</span><span class="sxs-lookup"><span data-stu-id="afe44-233">dotnet migrate</span></span>](dotnet-migrate.md) | <span data-ttu-id="afe44-234">Migruje prawidłowy projekt w wersji zapoznawczej 2 do projektu zestaw .NET Core SDK 1,0.</span><span class="sxs-lookup"><span data-stu-id="afe44-234">Migrates a valid Preview 2 project to a .NET Core SDK 1.0 project.</span></span>  |
| [<span data-ttu-id="afe44-235">dotnet msbuild</span><span class="sxs-lookup"><span data-stu-id="afe44-235">dotnet msbuild</span></span>](dotnet-msbuild.md) | <span data-ttu-id="afe44-236">Zapewnia dostęp do wiersza polecenia programu MSBuild.</span><span class="sxs-lookup"><span data-stu-id="afe44-236">Provides access to the MSBuild command line.</span></span>                        |
| [<span data-ttu-id="afe44-237">dotnet new</span><span class="sxs-lookup"><span data-stu-id="afe44-237">dotnet new</span></span>](dotnet-new.md)         | <span data-ttu-id="afe44-238">Inicjuje projekt C# lub F# dla danego szablonu.</span><span class="sxs-lookup"><span data-stu-id="afe44-238">Initializes a C# or F# project for a given template.</span></span>                |
| [<span data-ttu-id="afe44-239">dotnet pack</span><span class="sxs-lookup"><span data-stu-id="afe44-239">dotnet pack</span></span>](dotnet-pack.md)       | <span data-ttu-id="afe44-240">Tworzy pakiet NuGet kodu.</span><span class="sxs-lookup"><span data-stu-id="afe44-240">Creates a NuGet package of your code.</span></span>                               |
| [<span data-ttu-id="afe44-241">dotnet publish</span><span class="sxs-lookup"><span data-stu-id="afe44-241">dotnet publish</span></span>](dotnet-publish.md) | <span data-ttu-id="afe44-242">Publikuje zależne od programu .NET Framework lub samodzielną aplikację.</span><span class="sxs-lookup"><span data-stu-id="afe44-242">Publishes a .NET framework-dependent or self-contained application.</span></span> |
| [<span data-ttu-id="afe44-243">dotnet restore</span><span class="sxs-lookup"><span data-stu-id="afe44-243">dotnet restore</span></span>](dotnet-restore.md) | <span data-ttu-id="afe44-244">Przywraca zależności dla danej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="afe44-244">Restores the dependencies for a given application.</span></span>                  |
| [<span data-ttu-id="afe44-245">dotnet run</span><span class="sxs-lookup"><span data-stu-id="afe44-245">dotnet run</span></span>](dotnet-run.md)         | <span data-ttu-id="afe44-246">Uruchamia aplikację ze źródła.</span><span class="sxs-lookup"><span data-stu-id="afe44-246">Runs the application from source.</span></span>                                   |
| [<span data-ttu-id="afe44-247">dotnet sln</span><span class="sxs-lookup"><span data-stu-id="afe44-247">dotnet sln</span></span>](dotnet-sln.md)         | <span data-ttu-id="afe44-248">Opcje dodawania, usuwania i wyświetlania listy projektów w pliku rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="afe44-248">Options to add, remove, and list projects in a solution file.</span></span>       |
| [<span data-ttu-id="afe44-249">dotnet test</span><span class="sxs-lookup"><span data-stu-id="afe44-249">dotnet test</span></span>](dotnet-test.md)       | <span data-ttu-id="afe44-250">Uruchamia testy przy użyciu modułu uruchamiającego testy.</span><span class="sxs-lookup"><span data-stu-id="afe44-250">Runs tests using a test runner.</span></span>                                     |

---

### <a name="project-references"></a><span data-ttu-id="afe44-251">Odwołania projektu</span><span class="sxs-lookup"><span data-stu-id="afe44-251">Project references</span></span>

<span data-ttu-id="afe44-252">Polecenie</span><span class="sxs-lookup"><span data-stu-id="afe44-252">Command</span></span> | <span data-ttu-id="afe44-253">Funkcja</span><span class="sxs-lookup"><span data-stu-id="afe44-253">Function</span></span>
--- | ---
[<span data-ttu-id="afe44-254">dotnet add reference</span><span class="sxs-lookup"><span data-stu-id="afe44-254">dotnet add reference</span></span>](dotnet-add-reference.md) | <span data-ttu-id="afe44-255">Dodaje odwołanie do projektu.</span><span class="sxs-lookup"><span data-stu-id="afe44-255">Adds a project reference.</span></span>
[<span data-ttu-id="afe44-256">dotnet list reference</span><span class="sxs-lookup"><span data-stu-id="afe44-256">dotnet list reference</span></span>](dotnet-list-reference.md) | <span data-ttu-id="afe44-257">Wyświetla listę odwołań do projektu.</span><span class="sxs-lookup"><span data-stu-id="afe44-257">Lists project references.</span></span>
[<span data-ttu-id="afe44-258">dotnet remove reference</span><span class="sxs-lookup"><span data-stu-id="afe44-258">dotnet remove reference</span></span>](dotnet-remove-reference.md) | <span data-ttu-id="afe44-259">Usuwa odwołanie do projektu.</span><span class="sxs-lookup"><span data-stu-id="afe44-259">Removes a project reference.</span></span>

### <a name="nuget-packages"></a><span data-ttu-id="afe44-260">Pakiety NuGet</span><span class="sxs-lookup"><span data-stu-id="afe44-260">NuGet packages</span></span>

<span data-ttu-id="afe44-261">Polecenie</span><span class="sxs-lookup"><span data-stu-id="afe44-261">Command</span></span> | <span data-ttu-id="afe44-262">Funkcja</span><span class="sxs-lookup"><span data-stu-id="afe44-262">Function</span></span>
--- | ---
[<span data-ttu-id="afe44-263">dotnet add package</span><span class="sxs-lookup"><span data-stu-id="afe44-263">dotnet add package</span></span>](dotnet-add-package.md) | <span data-ttu-id="afe44-264">Dodaje pakiet NuGet.</span><span class="sxs-lookup"><span data-stu-id="afe44-264">Adds a NuGet package.</span></span>
[<span data-ttu-id="afe44-265">dotnet remove package</span><span class="sxs-lookup"><span data-stu-id="afe44-265">dotnet remove package</span></span>](dotnet-remove-package.md) | <span data-ttu-id="afe44-266">Usuwa pakiet NuGet.</span><span class="sxs-lookup"><span data-stu-id="afe44-266">Removes a NuGet package.</span></span>

### <a name="nuget-commands"></a><span data-ttu-id="afe44-267">Polecenia NuGet</span><span class="sxs-lookup"><span data-stu-id="afe44-267">NuGet commands</span></span>

<span data-ttu-id="afe44-268">Polecenie</span><span class="sxs-lookup"><span data-stu-id="afe44-268">Command</span></span> | <span data-ttu-id="afe44-269">Funkcja</span><span class="sxs-lookup"><span data-stu-id="afe44-269">Function</span></span>
--- | ---
[<span data-ttu-id="afe44-270">dotnet nuget delete</span><span class="sxs-lookup"><span data-stu-id="afe44-270">dotnet nuget delete</span></span>](dotnet-nuget-delete.md) | <span data-ttu-id="afe44-271">Usuwa pakiet z serwera lub go wystawia.</span><span class="sxs-lookup"><span data-stu-id="afe44-271">Deletes or unlists a package from the server.</span></span>
[<span data-ttu-id="afe44-272">dotnet nuget locals</span><span class="sxs-lookup"><span data-stu-id="afe44-272">dotnet nuget locals</span></span>](dotnet-nuget-locals.md) | <span data-ttu-id="afe44-273">Czyści lub wyświetla lokalne zasoby NuGet, takie jak pamięć podręczna żądań HTTP, tymczasowa pamięć podręczna lub folder pakietów globalnych dla całego komputera.</span><span class="sxs-lookup"><span data-stu-id="afe44-273">Clears or lists local NuGet resources such as http-request cache, temporary cache, or machine-wide global packages folder.</span></span>
[<span data-ttu-id="afe44-274">dotnet nuget push</span><span class="sxs-lookup"><span data-stu-id="afe44-274">dotnet nuget push</span></span>](dotnet-nuget-push.md) | <span data-ttu-id="afe44-275">Wypchnij pakiet na serwer i opublikuje go.</span><span class="sxs-lookup"><span data-stu-id="afe44-275">Pushes a package to the server and publishes it.</span></span>

### <a name="global-tools-commands"></a><span data-ttu-id="afe44-276">Polecenia narzędzi globalnych</span><span class="sxs-lookup"><span data-stu-id="afe44-276">Global Tools commands</span></span>

<span data-ttu-id="afe44-277">[Narzędzia globalne platformy .NET Core](global-tools.md) są dostępne począwszy od zestaw .NET Core SDK 2.1.300:</span><span class="sxs-lookup"><span data-stu-id="afe44-277">[.NET Core Global Tools](global-tools.md) are available starting with .NET Core SDK 2.1.300:</span></span>

<span data-ttu-id="afe44-278">Polecenie</span><span class="sxs-lookup"><span data-stu-id="afe44-278">Command</span></span> | <span data-ttu-id="afe44-279">Funkcja</span><span class="sxs-lookup"><span data-stu-id="afe44-279">Function</span></span>
--- | ---
[<span data-ttu-id="afe44-280">dotnet tool install</span><span class="sxs-lookup"><span data-stu-id="afe44-280">dotnet tool install</span></span>](dotnet-tool-install.md) | <span data-ttu-id="afe44-281">Instaluje narzędzie globalne na komputerze.</span><span class="sxs-lookup"><span data-stu-id="afe44-281">Installs a Global Tool on your machine.</span></span>
[<span data-ttu-id="afe44-282">dotnet tool list</span><span class="sxs-lookup"><span data-stu-id="afe44-282">dotnet tool list</span></span>](dotnet-tool-list.md) | <span data-ttu-id="afe44-283">Wyświetla listę wszystkich narzędzi globalnych aktualnie zainstalowanych w domyślnym katalogu na komputerze lub w określonej ścieżce.</span><span class="sxs-lookup"><span data-stu-id="afe44-283">Lists all Global Tools currently installed in the default directory on your machine or in the specified path.</span></span>
[<span data-ttu-id="afe44-284">dotnet tool uninstall</span><span class="sxs-lookup"><span data-stu-id="afe44-284">dotnet tool uninstall</span></span>](dotnet-tool-uninstall.md) | <span data-ttu-id="afe44-285">Odinstalowuje narzędzie globalne z komputera.</span><span class="sxs-lookup"><span data-stu-id="afe44-285">Uninstalls a Global Tool from your machine.</span></span>
[<span data-ttu-id="afe44-286">dotnet tool update</span><span class="sxs-lookup"><span data-stu-id="afe44-286">dotnet tool update</span></span>](dotnet-tool-update.md) | <span data-ttu-id="afe44-287">Aktualizuje narzędzie globalne na komputerze.</span><span class="sxs-lookup"><span data-stu-id="afe44-287">Updates a Global Tool on your machine.</span></span>

### <a name="additional-tools"></a><span data-ttu-id="afe44-288">Dodatkowe narzędzia</span><span class="sxs-lookup"><span data-stu-id="afe44-288">Additional tools</span></span>

<span data-ttu-id="afe44-289">Począwszy od zestaw .NET Core SDK 2.1.300, wiele narzędzi, które były dostępne tylko dla każdego projektu, przy użyciu `DotnetCliToolReference` , jest teraz dostępne jako część zestaw .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="afe44-289">Starting with .NET Core SDK 2.1.300, a number of tools that were available only on a per project basis using `DotnetCliToolReference` are now available as part of the .NET Core SDK.</span></span> <span data-ttu-id="afe44-290">Te narzędzia są wymienione w poniższej tabeli:</span><span class="sxs-lookup"><span data-stu-id="afe44-290">These tools are listed in the following table:</span></span>

| <span data-ttu-id="afe44-291">Narzędzie</span><span class="sxs-lookup"><span data-stu-id="afe44-291">Tool</span></span>                                              | <span data-ttu-id="afe44-292">Funkcja</span><span class="sxs-lookup"><span data-stu-id="afe44-292">Function</span></span>                                                     |
| ------------------------------------------------- | ------------------------------------------------------------ |
| <span data-ttu-id="afe44-293">dev-certs</span><span class="sxs-lookup"><span data-stu-id="afe44-293">dev-certs</span></span>                                         | <span data-ttu-id="afe44-294">Tworzy i zarządza certyfikatami deweloperskimi.</span><span class="sxs-lookup"><span data-stu-id="afe44-294">Creates and manages development certificates.</span></span>                |
| [<span data-ttu-id="afe44-295">bieżąco</span><span class="sxs-lookup"><span data-stu-id="afe44-295">ef</span></span>](/ef/core/miscellaneous/cli/dotnet)           | <span data-ttu-id="afe44-296">Entity Framework Core narzędzia wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="afe44-296">Entity Framework Core command-line tools.</span></span>                    |
| <span data-ttu-id="afe44-297">SQL-pamięć podręczna</span><span class="sxs-lookup"><span data-stu-id="afe44-297">sql-cache</span></span>                                         | <span data-ttu-id="afe44-298">SQL Server narzędzia wiersza polecenia pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="afe44-298">SQL Server cache command-line tools.</span></span>                         |
| [<span data-ttu-id="afe44-299">wpisy tajne użytkownika</span><span class="sxs-lookup"><span data-stu-id="afe44-299">user-secrets</span></span>](/aspnet/core/security/app-secrets) | <span data-ttu-id="afe44-300">Zarządza kluczami tajnymi użytkowników deweloperskich.</span><span class="sxs-lookup"><span data-stu-id="afe44-300">Manages development user secrets.</span></span>                            |
| [<span data-ttu-id="afe44-301">Obejrzyj</span><span class="sxs-lookup"><span data-stu-id="afe44-301">watch</span></span>](/aspnet/core/tutorials/dotnet-watch)      | <span data-ttu-id="afe44-302">Uruchamia obserwatora plików, który uruchamia polecenie, gdy pliki zmienią się.</span><span class="sxs-lookup"><span data-stu-id="afe44-302">Starts a file watcher that runs a command when files change.</span></span> |

<span data-ttu-id="afe44-303">Aby uzyskać więcej informacji na temat każdego narzędzia `dotnet <tool-name> --help`, wpisz.</span><span class="sxs-lookup"><span data-stu-id="afe44-303">For more information about each tool, type `dotnet <tool-name> --help`.</span></span>

## <a name="examples"></a><span data-ttu-id="afe44-304">Przykłady</span><span class="sxs-lookup"><span data-stu-id="afe44-304">Examples</span></span>

<span data-ttu-id="afe44-305">Tworzy nową aplikację konsolową platformy .NET Core:</span><span class="sxs-lookup"><span data-stu-id="afe44-305">Creates a new .NET Core console application:</span></span>

`dotnet new console`

<span data-ttu-id="afe44-306">Przywróć zależności dla danej aplikacji:</span><span class="sxs-lookup"><span data-stu-id="afe44-306">Restore dependencies for a given application:</span></span>

`dotnet restore`

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

<span data-ttu-id="afe44-307">Kompiluj projekt i jego zależności w danym katalogu:</span><span class="sxs-lookup"><span data-stu-id="afe44-307">Build a project and its dependencies in a given directory:</span></span>

`dotnet build`

<span data-ttu-id="afe44-308">Uruchom bibliotekę DLL aplikacji, na `myapp.dll`przykład:</span><span class="sxs-lookup"><span data-stu-id="afe44-308">Run an application DLL, such as `myapp.dll`:</span></span>

`dotnet myapp.dll`

## <a name="environment-variables"></a><span data-ttu-id="afe44-309">Zmienne środowiskowe</span><span class="sxs-lookup"><span data-stu-id="afe44-309">Environment variables</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="afe44-310">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="afe44-310">.NET Core 2.1</span></span>](#tab/netcore21)

`DOTNET_PACKAGES`

<span data-ttu-id="afe44-311">Folder pakiety globalne.</span><span class="sxs-lookup"><span data-stu-id="afe44-311">The global packages folder.</span></span> <span data-ttu-id="afe44-312">Jeśli nie jest ustawiona, zostanie ona `~/.nuget/packages` domyślnie włączona w `%userprofile%\.nuget\packages` systemie UNIX lub w systemie Windows.</span><span class="sxs-lookup"><span data-stu-id="afe44-312">If not set, it defaults to `~/.nuget/packages` on Unix or `%userprofile%\.nuget\packages` on Windows.</span></span>

`DOTNET_SERVICING`

<span data-ttu-id="afe44-313">Określa lokalizację indeksu obsługi, który ma być używany przez host udostępniony podczas ładowania środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="afe44-313">Specifies the location of the servicing index to use by the shared host when loading the runtime.</span></span>

`DOTNET_CLI_TELEMETRY_OPTOUT`

<span data-ttu-id="afe44-314">Określa, czy dane dotyczące użycia narzędzi .NET Core są zbierane i wysyłane do firmy Microsoft.</span><span class="sxs-lookup"><span data-stu-id="afe44-314">Specifies whether data about the .NET Core tools usage is collected and sent to Microsoft.</span></span> <span data-ttu-id="afe44-315">Ustaw, `true` aby zrezygnować z funkcji telemetrii (wartości `true`, `1`lub `yes` zaakceptować).</span><span class="sxs-lookup"><span data-stu-id="afe44-315">Set to `true` to opt-out of the telemetry feature (values `true`, `1`, or `yes` accepted).</span></span> <span data-ttu-id="afe44-316">W przeciwnym razie ustaw `false` opcję, aby można było wybrać funkcje telemetrii ( `no` wartości `false`, `0`lub zaakceptowane).</span><span class="sxs-lookup"><span data-stu-id="afe44-316">Otherwise, set to `false` to opt into the telemetry features (values `false`, `0`, or `no` accepted).</span></span> <span data-ttu-id="afe44-317">Jeśli nie zostanie ustawiona, wartość domyślna `false` to i aktywna funkcja telemetrii.</span><span class="sxs-lookup"><span data-stu-id="afe44-317">If not set, the default is `false` and the telemetry feature is active.</span></span>

`DOTNET_MULTILEVEL_LOOKUP`

<span data-ttu-id="afe44-318">Określa, czy środowisko uruchomieniowe programu .NET Core, udostępnione środowisko lub zestaw SDK są rozpoznawane z lokalizacji globalnej.</span><span class="sxs-lookup"><span data-stu-id="afe44-318">Specifies whether .NET Core runtime, shared framework, or SDK are resolved from the global location.</span></span> <span data-ttu-id="afe44-319">Jeśli nie zostanie ustawiona, domyślnie `true`jest to.</span><span class="sxs-lookup"><span data-stu-id="afe44-319">If not set, it defaults to `true`.</span></span> <span data-ttu-id="afe44-320">Ustawiona na `false` wartość nie jest rozpoznawana z lokalizacji globalnej i ma wyizolowane instalacje .NET `0` Core `false` (wartości lub są akceptowane).</span><span class="sxs-lookup"><span data-stu-id="afe44-320">Set to `false` to not resolve from the global location and have isolated .NET Core installations (values `0` or `false` are accepted).</span></span> <span data-ttu-id="afe44-321">Aby uzyskać więcej informacji o wyszukiwaniu wielu poziomów, zobacz [SharedFX wyszukiwanie na wielu poziomach](https://github.com/dotnet/core-setup/blob/master/Documentation/design-docs/multilevel-sharedfx-lookup.md).</span><span class="sxs-lookup"><span data-stu-id="afe44-321">For more information about multi-level lookup, see [Multi-level SharedFX Lookup](https://github.com/dotnet/core-setup/blob/master/Documentation/design-docs/multilevel-sharedfx-lookup.md).</span></span>

`DOTNET_ROLL_FORWARD_ON_NO_CANDIDATE_FX`

<span data-ttu-id="afe44-322">Wyłącza dodatkową wersję do przodu, jeśli jest ustawiona `0`na.</span><span class="sxs-lookup"><span data-stu-id="afe44-322">Disables minor version roll forward, if set to `0`.</span></span> <span data-ttu-id="afe44-323">Aby uzyskać więcej informacji, zobacz [przewinięcie do przodu](../whats-new/dotnet-core-2-1.md#roll-forward).</span><span class="sxs-lookup"><span data-stu-id="afe44-323">For more information, see [Roll forward](../whats-new/dotnet-core-2-1.md#roll-forward).</span></span>

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="afe44-324">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="afe44-324">.NET Core 2.0</span></span>](#tab/netcore20)

`DOTNET_PACKAGES`

<span data-ttu-id="afe44-325">Podstawowa pamięć podręczna pakietu.</span><span class="sxs-lookup"><span data-stu-id="afe44-325">The primary package cache.</span></span> <span data-ttu-id="afe44-326">Jeśli nie jest ustawiona, zostanie ona `$HOME/.nuget/packages` domyślnie włączona w `%userprofile%\.nuget\packages` systemie UNIX lub w systemie Windows.</span><span class="sxs-lookup"><span data-stu-id="afe44-326">If not set, it defaults to `$HOME/.nuget/packages` on Unix or `%userprofile%\.nuget\packages` on Windows.</span></span>

`DOTNET_SERVICING`

<span data-ttu-id="afe44-327">Określa lokalizację indeksu obsługi, który ma być używany przez host udostępniony podczas ładowania środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="afe44-327">Specifies the location of the servicing index to use by the shared host when loading the runtime.</span></span>

`DOTNET_CLI_TELEMETRY_OPTOUT`

<span data-ttu-id="afe44-328">Określa, czy dane dotyczące użycia narzędzi .NET Core są zbierane i wysyłane do firmy Microsoft.</span><span class="sxs-lookup"><span data-stu-id="afe44-328">Specifies whether data about the .NET Core tools usage is collected and sent to Microsoft.</span></span> <span data-ttu-id="afe44-329">Ustaw, `true` aby zrezygnować z funkcji telemetrii (wartości `true`, `1`lub `yes` zaakceptować).</span><span class="sxs-lookup"><span data-stu-id="afe44-329">Set to `true` to opt-out of the telemetry feature (values `true`, `1`, or `yes` accepted).</span></span> <span data-ttu-id="afe44-330">W przeciwnym razie ustaw `false` opcję, aby można było wybrać funkcje telemetrii ( `no` wartości `false`, `0`lub zaakceptowane).</span><span class="sxs-lookup"><span data-stu-id="afe44-330">Otherwise, set to `false` to opt into the telemetry features (values `false`, `0`, or `no` accepted).</span></span> <span data-ttu-id="afe44-331">Jeśli nie zostanie ustawiona, wartość domyślna `false` to i aktywna funkcja telemetrii.</span><span class="sxs-lookup"><span data-stu-id="afe44-331">If not set, the default is `false` and the telemetry feature is active.</span></span>

`DOTNET_MULTILEVEL_LOOKUP`

<span data-ttu-id="afe44-332">Określa, czy środowisko uruchomieniowe programu .NET Core, udostępnione środowisko lub zestaw SDK są rozpoznawane z lokalizacji globalnej.</span><span class="sxs-lookup"><span data-stu-id="afe44-332">Specifies whether .NET Core runtime, shared framework, or SDK are resolved from the global location.</span></span> <span data-ttu-id="afe44-333">Jeśli nie zostanie ustawiona, domyślnie `true`jest to.</span><span class="sxs-lookup"><span data-stu-id="afe44-333">If not set, it defaults to `true`.</span></span> <span data-ttu-id="afe44-334">Ustawiona na `false` wartość nie jest rozpoznawana z lokalizacji globalnej i ma wyizolowane instalacje .NET `0` Core `false` (wartości lub są akceptowane).</span><span class="sxs-lookup"><span data-stu-id="afe44-334">Set to `false` to not resolve from the global location and have isolated .NET Core installations (values `0` or `false` are accepted).</span></span> <span data-ttu-id="afe44-335">Aby uzyskać więcej informacji o wyszukiwaniu wielu poziomów, zobacz [SharedFX wyszukiwanie na wielu poziomach](https://github.com/dotnet/core-setup/blob/master/Documentation/design-docs/multilevel-sharedfx-lookup.md).</span><span class="sxs-lookup"><span data-stu-id="afe44-335">For more information about multi-level lookup, see [Multi-level SharedFX Lookup](https://github.com/dotnet/core-setup/blob/master/Documentation/design-docs/multilevel-sharedfx-lookup.md).</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="afe44-336">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="afe44-336">.NET Core 1.x</span></span>](#tab/netcore1x)

`DOTNET_PACKAGES`

<span data-ttu-id="afe44-337">Podstawowa pamięć podręczna pakietu.</span><span class="sxs-lookup"><span data-stu-id="afe44-337">The primary package cache.</span></span> <span data-ttu-id="afe44-338">Jeśli nie jest ustawiona, zostanie ona `$HOME/.nuget/packages` domyślnie włączona w `%userprofile%\.nuget\packages` systemie UNIX lub w systemie Windows.</span><span class="sxs-lookup"><span data-stu-id="afe44-338">If not set, it defaults to `$HOME/.nuget/packages` on Unix or `%userprofile%\.nuget\packages` on Windows.</span></span>

`DOTNET_SERVICING`

<span data-ttu-id="afe44-339">Określa lokalizację indeksu obsługi, który ma być używany przez host udostępniony podczas ładowania środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="afe44-339">Specifies the location of the servicing index to use by the shared host when loading the runtime.</span></span>

`DOTNET_CLI_TELEMETRY_OPTOUT`

<span data-ttu-id="afe44-340">Określa, czy dane dotyczące użycia narzędzi .NET Core są zbierane i wysyłane do firmy Microsoft.</span><span class="sxs-lookup"><span data-stu-id="afe44-340">Specifies whether data about the .NET Core tools usage is collected and sent to Microsoft.</span></span> <span data-ttu-id="afe44-341">Ustaw, `true` aby zrezygnować z funkcji telemetrii (wartości `true`, `1`lub `yes` zaakceptować).</span><span class="sxs-lookup"><span data-stu-id="afe44-341">Set to `true` to opt-out of the telemetry feature (values `true`, `1`, or `yes` accepted).</span></span> <span data-ttu-id="afe44-342">W przeciwnym razie ustaw `false` opcję, aby można było wybrać funkcje telemetrii ( `no` wartości `false`, `0`lub zaakceptowane).</span><span class="sxs-lookup"><span data-stu-id="afe44-342">Otherwise, set to `false` to opt into the telemetry features (values `false`, `0`, or `no` accepted).</span></span> <span data-ttu-id="afe44-343">Jeśli nie zostanie ustawiona, wartość domyślna `false` to i aktywna funkcja telemetrii.</span><span class="sxs-lookup"><span data-stu-id="afe44-343">If not set, the default is `false` and the telemetry feature is active.</span></span>

---
