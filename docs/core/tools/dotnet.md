---
title: polecenie DotNet - .NET Core interfejsu wiersza polecenia
description: Informacje o poleceniu dotnet (ogólnego sterownik narzędzi interfejsu wiersza polecenia platformy .NET Core) i jej użycia.
author: mairaw
ms.author: mairaw
ms.date: 03/20/2018
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.workload:
- dotnetcore
ms.openlocfilehash: 2d22124cb613152df402046541650f3262e7e202
ms.sourcegitcommit: 6f967c86dde55472440f0c8669b0e910ee3c53ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2018
---
# <a name="dotnet-command"></a><span data-ttu-id="45ad3-103">polecenie DotNet</span><span class="sxs-lookup"><span data-stu-id="45ad3-103">dotnet command</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="45ad3-104">Nazwa</span><span class="sxs-lookup"><span data-stu-id="45ad3-104">Name</span></span>

<span data-ttu-id="45ad3-105">`dotnet` -Ogólne sterownik do uruchamiania polecenia wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="45ad3-105">`dotnet` - General driver for running the command-line commands.</span></span>

## <a name="synopsis"></a><span data-ttu-id="45ad3-106">Streszczenie</span><span class="sxs-lookup"><span data-stu-id="45ad3-106">Synopsis</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="45ad3-107">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="45ad3-107">.NET Core 2.x</span></span>](#tab/netcore2x)
```
dotnet [command] [arguments] [--additional-deps] [--additionalprobingpath] [-d|--diagnostics]
    [--fx-version] [-h|--help] [--info] [--roll-forward-on-no-candidate-fx] [-v|--verbosity] [--version]
```
# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="45ad3-108">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="45ad3-108">.NET Core 1.x</span></span>](#tab/netcore1x)
```
dotnet [command] [arguments] [--additionalprobingpath] [-d|--diagnostics] [--fx-version]
    [-h|--help] [--info] [-v|--verbosity] [--version]
```
---

## <a name="description"></a><span data-ttu-id="45ad3-109">Opis</span><span class="sxs-lookup"><span data-stu-id="45ad3-109">Description</span></span>

<span data-ttu-id="45ad3-110">`dotnet` jest ogólny sterownik łańcuch narzędzi interfejsu wiersza polecenia (CLI).</span><span class="sxs-lookup"><span data-stu-id="45ad3-110">`dotnet` is a generic driver for the Command Line Interface (CLI) toolchain.</span></span> <span data-ttu-id="45ad3-111">Wywoływane na jego własnej, zapewnia użycia krótkie instrukcje.</span><span class="sxs-lookup"><span data-stu-id="45ad3-111">Invoked on its own, it provides brief usage instructions.</span></span>

<span data-ttu-id="45ad3-112">Każdej z funkcji jest implementowany jako polecenia.</span><span class="sxs-lookup"><span data-stu-id="45ad3-112">Each specific feature is implemented as a command.</span></span> <span data-ttu-id="45ad3-113">Aby można było użyć funkcji, polecenie określono po `dotnet`, takich jak [ `dotnet build` ](dotnet-build.md).</span><span class="sxs-lookup"><span data-stu-id="45ad3-113">In order to use the feature, the command is specified after `dotnet`, such as [`dotnet build`](dotnet-build.md).</span></span> <span data-ttu-id="45ad3-114">Wszystkie argumenty następujące polecenie to własną argumentów.</span><span class="sxs-lookup"><span data-stu-id="45ad3-114">All of the arguments following the command are its own arguments.</span></span>

<span data-ttu-id="45ad3-115">Tylko `dotnet` jest używany jako polecenia samodzielnie [aplikacje zależne od framework](../deploying/index.md).</span><span class="sxs-lookup"><span data-stu-id="45ad3-115">The only time `dotnet` is used as a command on its own is to run [framework-dependent apps](../deploying/index.md).</span></span> <span data-ttu-id="45ad3-116">Określ aplikację DLL po `dotnet` zlecenie do wykonywania aplikacji (na przykład `dotnet myapp.dll`).</span><span class="sxs-lookup"><span data-stu-id="45ad3-116">Specify an application DLL after the `dotnet` verb to execute the application (for example, `dotnet myapp.dll`).</span></span>

## <a name="options"></a><span data-ttu-id="45ad3-117">Opcje</span><span class="sxs-lookup"><span data-stu-id="45ad3-117">Options</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="45ad3-118">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="45ad3-118">.NET Core 2.x</span></span>](#tab/netcore2x)

`--additional-deps <PATH>`

<span data-ttu-id="45ad3-119">Ścieżka do dodatkowych *deps.json* pliku.</span><span class="sxs-lookup"><span data-stu-id="45ad3-119">Path to additional *deps.json* file.</span></span>

`--additionalprobingpath <PATH>`

<span data-ttu-id="45ad3-120">Ścieżka zawierające sondowania zasad i zestawów do sondowania.</span><span class="sxs-lookup"><span data-stu-id="45ad3-120">Path containing probing policy and assemblies to probe.</span></span>

`-d|--diagnostics`

<span data-ttu-id="45ad3-121">Umożliwia wyjście diagnostyczne.</span><span class="sxs-lookup"><span data-stu-id="45ad3-121">Enables diagnostic output.</span></span>

`--fx-version <VERSION>`

<span data-ttu-id="45ad3-122">Wersja zainstalowanego środowiska uruchomieniowego .NET Core służące do uruchamiania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="45ad3-122">Version of the installed .NET Core runtime to use to run the application.</span></span>

`-h|--help`

<span data-ttu-id="45ad3-123">Drukuje krótkich pomocy dla polecenia.</span><span class="sxs-lookup"><span data-stu-id="45ad3-123">Prints out a short help for the command.</span></span> <span data-ttu-id="45ad3-124">Jeśli używany z `dotnet`, również Wyświetla listę dostępnych poleceń.</span><span class="sxs-lookup"><span data-stu-id="45ad3-124">If using with `dotnet`, it also prints a list of the available commands.</span></span>

`--info`

<span data-ttu-id="45ad3-125">Drukuje szczegółowe informacje na temat narzędzi interfejsu wiersza polecenia i środowiska, takich jak bieżący system operacyjny, Zatwierdź SHA dla wersji i innych informacji.</span><span class="sxs-lookup"><span data-stu-id="45ad3-125">Prints out detailed information about the CLI tooling and the environment, such as the current operating system, commit SHA for the version, and other information.</span></span>

`--roll-forward-on-no-candidate-fx`

 <span data-ttu-id="45ad3-126">Przedstawia przekazywania na ma kandydata framework udostępnionego.</span><span class="sxs-lookup"><span data-stu-id="45ad3-126">Rolls forward on no candidate shared framework.</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="45ad3-127">Ustawia poziom szczegółowości polecenia.</span><span class="sxs-lookup"><span data-stu-id="45ad3-127">Sets the verbosity level of the command.</span></span> <span data-ttu-id="45ad3-128">Dozwolone wartości to `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, i `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="45ad3-128">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="45ad3-129">Nie są obsługiwane w każdym poleceniu; zobacz stronę danego polecenia, aby ustalić, czy ta opcja jest dostępna.</span><span class="sxs-lookup"><span data-stu-id="45ad3-129">Not supported in every command; see specific command page to determine if this option is available.</span></span>

`--version`

<span data-ttu-id="45ad3-130">Drukuje wersji programu .NET Core SDK w użyciu.</span><span class="sxs-lookup"><span data-stu-id="45ad3-130">Prints out the version of the .NET Core SDK in use.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="45ad3-131">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="45ad3-131">.NET Core 1.x</span></span>](#tab/netcore1x)

`--additionalprobingpath <PATH>`

<span data-ttu-id="45ad3-132">Ścieżka zawierające sondowania zasad i zestawów do sondowania.</span><span class="sxs-lookup"><span data-stu-id="45ad3-132">Path containing probing policy and assemblies to probe.</span></span>

`-d|--diagnostics`

<span data-ttu-id="45ad3-133">Umożliwia wyjście diagnostyczne.</span><span class="sxs-lookup"><span data-stu-id="45ad3-133">Enables diagnostic output.</span></span>

`--fx-version <VERSION>`

<span data-ttu-id="45ad3-134">Wersja zainstalowanego środowiska uruchomieniowego .NET Core służące do uruchamiania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="45ad3-134">Version of the installed .NET Core runtime to use to run the application.</span></span>

`-h|--help`

<span data-ttu-id="45ad3-135">Drukuje krótkich pomocy dla polecenia.</span><span class="sxs-lookup"><span data-stu-id="45ad3-135">Prints out a short help for the command.</span></span> <span data-ttu-id="45ad3-136">Jeśli używany z `dotnet`, również Wyświetla listę dostępnych poleceń.</span><span class="sxs-lookup"><span data-stu-id="45ad3-136">If using with `dotnet`, it also prints a list of the available commands.</span></span>

`--info`

<span data-ttu-id="45ad3-137">Drukuje szczegółowe informacje na temat narzędzi interfejsu wiersza polecenia i środowiska, takich jak bieżący system operacyjny, Zatwierdź SHA dla wersji i innych informacji.</span><span class="sxs-lookup"><span data-stu-id="45ad3-137">Prints out detailed information about the CLI tooling and the environment, such as the current operating system, commit SHA for the version, and other information.</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="45ad3-138">Ustawia poziom szczegółowości polecenia.</span><span class="sxs-lookup"><span data-stu-id="45ad3-138">Sets the verbosity level of the command.</span></span> <span data-ttu-id="45ad3-139">Dozwolone wartości to `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, i `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="45ad3-139">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="45ad3-140">Nie są obsługiwane w każdym poleceniu; zobacz stronę danego polecenia, aby ustalić, czy ta opcja jest dostępna.</span><span class="sxs-lookup"><span data-stu-id="45ad3-140">Not supported in every command; see specific command page to determine if this option is available.</span></span>

`--version`

<span data-ttu-id="45ad3-141">Drukuje wersji programu .NET Core SDK w użyciu.</span><span class="sxs-lookup"><span data-stu-id="45ad3-141">Prints out the version of the .NET Core SDK in use.</span></span>

---

## <a name="dotnet-commands"></a><span data-ttu-id="45ad3-142">polecenia DotNet</span><span class="sxs-lookup"><span data-stu-id="45ad3-142">dotnet commands</span></span>

### <a name="general"></a><span data-ttu-id="45ad3-143">Ogólne</span><span class="sxs-lookup"><span data-stu-id="45ad3-143">General</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="45ad3-144">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="45ad3-144">.NET Core 2.x</span></span>](#tab/netcore2x)

| <span data-ttu-id="45ad3-145">Polecenie</span><span class="sxs-lookup"><span data-stu-id="45ad3-145">Command</span></span>                             | <span data-ttu-id="45ad3-146">Funkcja</span><span class="sxs-lookup"><span data-stu-id="45ad3-146">Function</span></span>                                                            |
| ----------------------------------- | ------------------------------------------------------------------- |
| [<span data-ttu-id="45ad3-147">dotnet build</span><span class="sxs-lookup"><span data-stu-id="45ad3-147">dotnet build</span></span>](dotnet-build.md)     | <span data-ttu-id="45ad3-148">Tworzy aplikacji .NET Core.</span><span class="sxs-lookup"><span data-stu-id="45ad3-148">Builds a .NET Core application.</span></span>                                     |
| [<span data-ttu-id="45ad3-149">dotnet clean</span><span class="sxs-lookup"><span data-stu-id="45ad3-149">dotnet clean</span></span>](dotnet-clean.md)     | <span data-ttu-id="45ad3-150">Wyczyść wyniki do kompilacji.</span><span class="sxs-lookup"><span data-stu-id="45ad3-150">Clean build outputs.</span></span>                                              |
| [<span data-ttu-id="45ad3-151">dotnet help</span><span class="sxs-lookup"><span data-stu-id="45ad3-151">dotnet help</span></span>](dotnet-help.md)       | <span data-ttu-id="45ad3-152">Przedstawia szczegółowe dokumentacji online dla polecenia.</span><span class="sxs-lookup"><span data-stu-id="45ad3-152">Shows more detailed documentation online for the command.</span></span>           |
| [<span data-ttu-id="45ad3-153">dotnet migrate</span><span class="sxs-lookup"><span data-stu-id="45ad3-153">dotnet migrate</span></span>](dotnet-migrate.md) | <span data-ttu-id="45ad3-154">Wykonuje migrację prawidłowy projekt Preview 2 projektu .NET Core SDK 1.0.</span><span class="sxs-lookup"><span data-stu-id="45ad3-154">Migrates a valid Preview 2 project to a .NET Core SDK 1.0 project.</span></span>  |
| [<span data-ttu-id="45ad3-155">dotnet msbuild</span><span class="sxs-lookup"><span data-stu-id="45ad3-155">dotnet msbuild</span></span>](dotnet-msbuild.md) | <span data-ttu-id="45ad3-156">Zapewnia dostęp do wiersza polecenia programu MSBuild.</span><span class="sxs-lookup"><span data-stu-id="45ad3-156">Provides access to the MSBuild command line.</span></span>                        |
| [<span data-ttu-id="45ad3-157">dotnet new</span><span class="sxs-lookup"><span data-stu-id="45ad3-157">dotnet new</span></span>](dotnet-new.md)         | <span data-ttu-id="45ad3-158">Inicjuje języka C# lub projektów F # dla danego szablonu.</span><span class="sxs-lookup"><span data-stu-id="45ad3-158">Initializes a C# or F# project for a given template.</span></span>                |
| [<span data-ttu-id="45ad3-159">dotnet pack</span><span class="sxs-lookup"><span data-stu-id="45ad3-159">dotnet pack</span></span>](dotnet-pack.md)       | <span data-ttu-id="45ad3-160">Tworzy pakiet NuGet kodu.</span><span class="sxs-lookup"><span data-stu-id="45ad3-160">Creates a NuGet package of your code.</span></span>                               |
| [<span data-ttu-id="45ad3-161">dotnet publish</span><span class="sxs-lookup"><span data-stu-id="45ad3-161">dotnet publish</span></span>](dotnet-publish.md) | <span data-ttu-id="45ad3-162">Publikowanie aplikacji .NET framework zależne lub niezależne.</span><span class="sxs-lookup"><span data-stu-id="45ad3-162">Publishes a .NET framework-dependent or self-contained application.</span></span> |
| [<span data-ttu-id="45ad3-163">dotnet restore</span><span class="sxs-lookup"><span data-stu-id="45ad3-163">dotnet restore</span></span>](dotnet-restore.md) | <span data-ttu-id="45ad3-164">Przywraca zależności dla danej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="45ad3-164">Restores the dependencies for a given application.</span></span>                  |
| [<span data-ttu-id="45ad3-165">dotnet run</span><span class="sxs-lookup"><span data-stu-id="45ad3-165">dotnet run</span></span>](dotnet-run.md)         | <span data-ttu-id="45ad3-166">Aplikacja jest uruchamiana ze źródła.</span><span class="sxs-lookup"><span data-stu-id="45ad3-166">Runs the application from source.</span></span>                                   |
| [<span data-ttu-id="45ad3-167">dotnet sln</span><span class="sxs-lookup"><span data-stu-id="45ad3-167">dotnet sln</span></span>](dotnet-sln.md)         | <span data-ttu-id="45ad3-168">Opcje do dodawania, usuwania i wyświetlić listę projektów w pliku rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="45ad3-168">Options to add, remove, and list projects in a solution file.</span></span>       |
| [<span data-ttu-id="45ad3-169">dotnet store</span><span class="sxs-lookup"><span data-stu-id="45ad3-169">dotnet store</span></span>](dotnet-store.md)     | <span data-ttu-id="45ad3-170">Przechowuje zestawy w magazynie pakietów środowiska wykonawczego.</span><span class="sxs-lookup"><span data-stu-id="45ad3-170">Stores assemblies in the runtime package store.</span></span>                     |
| [<span data-ttu-id="45ad3-171">dotnet test</span><span class="sxs-lookup"><span data-stu-id="45ad3-171">dotnet test</span></span>](dotnet-test.md)       | <span data-ttu-id="45ad3-172">Uruchamia testy przy użyciu runner testu.</span><span class="sxs-lookup"><span data-stu-id="45ad3-172">Runs tests using a test runner.</span></span>                                     |

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="45ad3-173">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="45ad3-173">.NET Core 1.x</span></span>](#tab/netcore1x)

| <span data-ttu-id="45ad3-174">Polecenie</span><span class="sxs-lookup"><span data-stu-id="45ad3-174">Command</span></span>                             | <span data-ttu-id="45ad3-175">Funkcja</span><span class="sxs-lookup"><span data-stu-id="45ad3-175">Function</span></span>                                                            |
| ----------------------------------- | ------------------------------------------------------------------- |
| [<span data-ttu-id="45ad3-176">dotnet build</span><span class="sxs-lookup"><span data-stu-id="45ad3-176">dotnet build</span></span>](dotnet-build.md)     | <span data-ttu-id="45ad3-177">Tworzy aplikacji .NET Core.</span><span class="sxs-lookup"><span data-stu-id="45ad3-177">Builds a .NET Core application.</span></span>                                     |
| [<span data-ttu-id="45ad3-178">dotnet clean</span><span class="sxs-lookup"><span data-stu-id="45ad3-178">dotnet clean</span></span>](dotnet-clean.md)     | <span data-ttu-id="45ad3-179">Wyczyść wyniki do kompilacji.</span><span class="sxs-lookup"><span data-stu-id="45ad3-179">Clean build outputs.</span></span>                                              |
| [<span data-ttu-id="45ad3-180">dotnet migrate</span><span class="sxs-lookup"><span data-stu-id="45ad3-180">dotnet migrate</span></span>](dotnet-migrate.md) | <span data-ttu-id="45ad3-181">Wykonuje migrację prawidłowy projekt Preview 2 projektu .NET Core SDK 1.0.</span><span class="sxs-lookup"><span data-stu-id="45ad3-181">Migrates a valid Preview 2 project to a .NET Core SDK 1.0 project.</span></span>  |
| [<span data-ttu-id="45ad3-182">dotnet msbuild</span><span class="sxs-lookup"><span data-stu-id="45ad3-182">dotnet msbuild</span></span>](dotnet-msbuild.md) | <span data-ttu-id="45ad3-183">Zapewnia dostęp do wiersza polecenia programu MSBuild.</span><span class="sxs-lookup"><span data-stu-id="45ad3-183">Provides access to the MSBuild command line.</span></span>                        |
| [<span data-ttu-id="45ad3-184">dotnet new</span><span class="sxs-lookup"><span data-stu-id="45ad3-184">dotnet new</span></span>](dotnet-new.md)         | <span data-ttu-id="45ad3-185">Inicjuje języka C# lub projektów F # dla danego szablonu.</span><span class="sxs-lookup"><span data-stu-id="45ad3-185">Initializes a C# or F# project for a given template.</span></span>                |
| [<span data-ttu-id="45ad3-186">dotnet pack</span><span class="sxs-lookup"><span data-stu-id="45ad3-186">dotnet pack</span></span>](dotnet-pack.md)       | <span data-ttu-id="45ad3-187">Tworzy pakiet NuGet kodu.</span><span class="sxs-lookup"><span data-stu-id="45ad3-187">Creates a NuGet package of your code.</span></span>                               |
| [<span data-ttu-id="45ad3-188">dotnet publish</span><span class="sxs-lookup"><span data-stu-id="45ad3-188">dotnet publish</span></span>](dotnet-publish.md) | <span data-ttu-id="45ad3-189">Publikowanie aplikacji .NET framework zależne lub niezależne.</span><span class="sxs-lookup"><span data-stu-id="45ad3-189">Publishes a .NET framework-dependent or self-contained application.</span></span> |
| [<span data-ttu-id="45ad3-190">dotnet restore</span><span class="sxs-lookup"><span data-stu-id="45ad3-190">dotnet restore</span></span>](dotnet-restore.md) | <span data-ttu-id="45ad3-191">Przywraca zależności dla danej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="45ad3-191">Restores the dependencies for a given application.</span></span>                  |
| [<span data-ttu-id="45ad3-192">dotnet run</span><span class="sxs-lookup"><span data-stu-id="45ad3-192">dotnet run</span></span>](dotnet-run.md)         | <span data-ttu-id="45ad3-193">Aplikacja jest uruchamiana ze źródła.</span><span class="sxs-lookup"><span data-stu-id="45ad3-193">Runs the application from source.</span></span>                                   |
| [<span data-ttu-id="45ad3-194">dotnet sln</span><span class="sxs-lookup"><span data-stu-id="45ad3-194">dotnet sln</span></span>](dotnet-sln.md)         | <span data-ttu-id="45ad3-195">Opcje do dodawania, usuwania i wyświetlić listę projektów w pliku rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="45ad3-195">Options to add, remove, and list projects in a solution file.</span></span>       |
| [<span data-ttu-id="45ad3-196">dotnet test</span><span class="sxs-lookup"><span data-stu-id="45ad3-196">dotnet test</span></span>](dotnet-test.md)       | <span data-ttu-id="45ad3-197">Uruchamia testy przy użyciu runner testu.</span><span class="sxs-lookup"><span data-stu-id="45ad3-197">Runs tests using a test runner.</span></span>                                     |

---

### <a name="project-references"></a><span data-ttu-id="45ad3-198">Odwołania do projektu</span><span class="sxs-lookup"><span data-stu-id="45ad3-198">Project references</span></span>

<span data-ttu-id="45ad3-199">Polecenie</span><span class="sxs-lookup"><span data-stu-id="45ad3-199">Command</span></span> | <span data-ttu-id="45ad3-200">Funkcja</span><span class="sxs-lookup"><span data-stu-id="45ad3-200">Function</span></span>
--- | ---
[<span data-ttu-id="45ad3-201">dotnet add reference</span><span class="sxs-lookup"><span data-stu-id="45ad3-201">dotnet add reference</span></span>](dotnet-add-reference.md) | <span data-ttu-id="45ad3-202">Dodaj odwołanie do projektu.</span><span class="sxs-lookup"><span data-stu-id="45ad3-202">Add a project reference.</span></span>
[<span data-ttu-id="45ad3-203">dotnet list reference</span><span class="sxs-lookup"><span data-stu-id="45ad3-203">dotnet list reference</span></span>](dotnet-list-reference.md) | <span data-ttu-id="45ad3-204">Lista odwołań do projektu.</span><span class="sxs-lookup"><span data-stu-id="45ad3-204">List project references.</span></span>
[<span data-ttu-id="45ad3-205">dotnet remove reference</span><span class="sxs-lookup"><span data-stu-id="45ad3-205">dotnet remove reference</span></span>](dotnet-remove-reference.md) | <span data-ttu-id="45ad3-206">Usuń odwołanie do projektu.</span><span class="sxs-lookup"><span data-stu-id="45ad3-206">Remove a project reference.</span></span>

### <a name="nuget-packages"></a><span data-ttu-id="45ad3-207">Pakiety NuGet</span><span class="sxs-lookup"><span data-stu-id="45ad3-207">NuGet packages</span></span>

<span data-ttu-id="45ad3-208">Polecenie</span><span class="sxs-lookup"><span data-stu-id="45ad3-208">Command</span></span> | <span data-ttu-id="45ad3-209">Funkcja</span><span class="sxs-lookup"><span data-stu-id="45ad3-209">Function</span></span>
--- | ---
[<span data-ttu-id="45ad3-210">dotnet add package</span><span class="sxs-lookup"><span data-stu-id="45ad3-210">dotnet add package</span></span>](dotnet-add-package.md) | <span data-ttu-id="45ad3-211">Dodaj pakiet NuGet.</span><span class="sxs-lookup"><span data-stu-id="45ad3-211">Add a NuGet package.</span></span>
[<span data-ttu-id="45ad3-212">dotnet remove package</span><span class="sxs-lookup"><span data-stu-id="45ad3-212">dotnet remove package</span></span>](dotnet-remove-package.md) | <span data-ttu-id="45ad3-213">Usunięcie pakietu NuGet.</span><span class="sxs-lookup"><span data-stu-id="45ad3-213">Remove a NuGet package.</span></span>

### <a name="nuget-commands"></a><span data-ttu-id="45ad3-214">Polecenia NuGet</span><span class="sxs-lookup"><span data-stu-id="45ad3-214">NuGet commands</span></span>

<span data-ttu-id="45ad3-215">Polecenie</span><span class="sxs-lookup"><span data-stu-id="45ad3-215">Command</span></span> | <span data-ttu-id="45ad3-216">Funkcja</span><span class="sxs-lookup"><span data-stu-id="45ad3-216">Function</span></span>
--- | ---
[<span data-ttu-id="45ad3-217">dotnet nuget delete</span><span class="sxs-lookup"><span data-stu-id="45ad3-217">dotnet nuget delete</span></span>](dotnet-nuget-delete.md) | <span data-ttu-id="45ad3-218">Usuwa lub unlists pakietu z serwera.</span><span class="sxs-lookup"><span data-stu-id="45ad3-218">Deletes or unlists a package from the server.</span></span>
[<span data-ttu-id="45ad3-219">dotnet nuget locals</span><span class="sxs-lookup"><span data-stu-id="45ad3-219">dotnet nuget locals</span></span>](dotnet-nuget-locals.md) | <span data-ttu-id="45ad3-220">Czyści lub wyświetla ich listę zasobów lokalnych NuGet np. pamięci podręcznej żądania http, tymczasowego pamięci podręcznej lub folderu packages globalne dla komputera.</span><span class="sxs-lookup"><span data-stu-id="45ad3-220">Clears or lists local NuGet resources such as http-request cache, temporary cache, or machine-wide global packages folder.</span></span>
[<span data-ttu-id="45ad3-221">dotnet nuget push</span><span class="sxs-lookup"><span data-stu-id="45ad3-221">dotnet nuget push</span></span>](dotnet-nuget-push.md) | <span data-ttu-id="45ad3-222">Wypychanie pakietu do serwera i publikuje ją.</span><span class="sxs-lookup"><span data-stu-id="45ad3-222">Pushes a package to the server and publishes it.</span></span>

## <a name="examples"></a><span data-ttu-id="45ad3-223">Przykłady</span><span class="sxs-lookup"><span data-stu-id="45ad3-223">Examples</span></span>

<span data-ttu-id="45ad3-224">Inicjowanie przykładowej aplikacji konsoli .NET Core, który można skompilować i uruchomić:</span><span class="sxs-lookup"><span data-stu-id="45ad3-224">Initialize a sample .NET Core console application that can be compiled and run:</span></span>

`dotnet new console`

<span data-ttu-id="45ad3-225">Przywróć zależności dla danej aplikacji:</span><span class="sxs-lookup"><span data-stu-id="45ad3-225">Restore dependencies for a given application:</span></span>

`dotnet restore`

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

<span data-ttu-id="45ad3-226">Tworzenie projektu i jego zależności w podanym katalogu:</span><span class="sxs-lookup"><span data-stu-id="45ad3-226">Build a project and its dependencies in a given directory:</span></span>

`dotnet build`

<span data-ttu-id="45ad3-227">Uruchamianie aplikacji zależnych od framework o nazwie `myapp.dll`:</span><span class="sxs-lookup"><span data-stu-id="45ad3-227">Run a framework-dependent app named `myapp.dll`:</span></span>

`dotnet myapp.dll`

## <a name="environment-variables"></a><span data-ttu-id="45ad3-228">Zmienne środowiskowe</span><span class="sxs-lookup"><span data-stu-id="45ad3-228">Environment variables</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="45ad3-229">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="45ad3-229">.NET Core 2.x</span></span>](#tab/netcore2x)

`DOTNET_PACKAGES`

<span data-ttu-id="45ad3-230">Pakiet główny pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="45ad3-230">The primary package cache.</span></span> <span data-ttu-id="45ad3-231">Jeśli nie został ustawiony, domyślnie `$HOME/.nuget/packages` w systemie Unix lub `%HOME%\NuGet\Packages` w systemie Windows.</span><span class="sxs-lookup"><span data-stu-id="45ad3-231">If not set, it defaults to `$HOME/.nuget/packages` on Unix or `%HOME%\NuGet\Packages` on Windows.</span></span>

`DOTNET_SERVICING`

<span data-ttu-id="45ad3-232">Określa lokalizację obsługi indeksu jest używany przez hosta udostępnionych podczas ładowania środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="45ad3-232">Specifies the location of the servicing index to use by the shared host when loading the runtime.</span></span>

`DOTNET_CLI_TELEMETRY_OPTOUT`

<span data-ttu-id="45ad3-233">Określa, czy dane dotyczące użycia narzędzia .NET Core został zebrany i wysyłany do firmy Microsoft.</span><span class="sxs-lookup"><span data-stu-id="45ad3-233">Specifies whether data about the .NET Core tools usage is collected and sent to Microsoft.</span></span> <span data-ttu-id="45ad3-234">Ustaw `true` Aby zrezygnować z funkcji telemetrii (wartości `true`, `1`, lub `yes` zaakceptowane), w przeciwnym razie należy ustawić `false` w funkcji telemetrii (wartości `false`, `0`, lub `no` akceptowane).</span><span class="sxs-lookup"><span data-stu-id="45ad3-234">Set to `true` to opt-out of the telemetry feature (values `true`, `1`, or `yes` accepted); otherwise, set to `false` to opt-in to the telemetry features (values `false`, `0`, or `no` accepted).</span></span> <span data-ttu-id="45ad3-235">Jeśli nie jest ustawiony, wartości domyślne jest `false`, i funkcja telemetrii jest aktywna.</span><span class="sxs-lookup"><span data-stu-id="45ad3-235">If not set, the defaults is `false`, and the telemetry feature is active.</span></span>

`DOTNET_MULTILEVEL_LOOKUP`

<span data-ttu-id="45ad3-236">Określa, czy podstawowego środowiska wykonawczego .NET, udostępnionych framework lub zestawu SDK są rozpoznane w globalnej lokalizacji.</span><span class="sxs-lookup"><span data-stu-id="45ad3-236">Specifies whether .NET Core runtime, shared framework or SDK are resolved from the global location.</span></span> <span data-ttu-id="45ad3-237">Jeśli nie jest ustawiona, domyślne `true`.</span><span class="sxs-lookup"><span data-stu-id="45ad3-237">If not set, it defaults to `true`.</span></span> <span data-ttu-id="45ad3-238">Ustaw `false` rozwiązania z globalnej lokalizacji i mają odizolowane instalacji platformy .NET Core (wartości `0` lub `false` są akceptowane).</span><span class="sxs-lookup"><span data-stu-id="45ad3-238">Set to `false` to not resolve from the global location and have isolated .NET Core installations (values `0` or `false` are accepted).</span></span> <span data-ttu-id="45ad3-239">Aby uzyskać więcej informacji na temat wyszukiwania wielopoziomowe zobacz [wyszukiwania SharedFX wielopoziomowej](https://github.com/dotnet/core-setup/blob/master/Documentation/design-docs/multilevel-sharedfx-lookup.md).</span><span class="sxs-lookup"><span data-stu-id="45ad3-239">For more information about multi-level lookup, see [Multi-level SharedFX Lookup](https://github.com/dotnet/core-setup/blob/master/Documentation/design-docs/multilevel-sharedfx-lookup.md).</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="45ad3-240">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="45ad3-240">.NET Core 1.x</span></span>](#tab/netcore1x)

`DOTNET_PACKAGES`

<span data-ttu-id="45ad3-241">Pakiet główny pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="45ad3-241">The primary package cache.</span></span> <span data-ttu-id="45ad3-242">Jeśli nie został ustawiony, domyślnie `$HOME/.nuget/packages` w systemie Unix lub `%HOME%\NuGet\Packages` w systemie Windows.</span><span class="sxs-lookup"><span data-stu-id="45ad3-242">If not set, it defaults to `$HOME/.nuget/packages` on Unix or `%HOME%\NuGet\Packages` on Windows.</span></span>

`DOTNET_SERVICING`

<span data-ttu-id="45ad3-243">Określa lokalizację obsługi indeksu jest używany przez hosta udostępnionych podczas ładowania środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="45ad3-243">Specifies the location of the servicing index to use by the shared host when loading the runtime.</span></span>

`DOTNET_CLI_TELEMETRY_OPTOUT`

<span data-ttu-id="45ad3-244">Określa, czy dane dotyczące użycia narzędzia .NET Core został zebrany i wysyłany do firmy Microsoft.</span><span class="sxs-lookup"><span data-stu-id="45ad3-244">Specifies whether data about the .NET Core tools usage is collected and sent to Microsoft.</span></span> <span data-ttu-id="45ad3-245">Ustaw `true` Aby zrezygnować z funkcji telemetrii (wartości `true`, `1`, lub `yes` zaakceptowane), w przeciwnym razie należy ustawić `false` w funkcji telemetrii (wartości `false`, `0`, lub `no` akceptowane).</span><span class="sxs-lookup"><span data-stu-id="45ad3-245">Set to `true` to opt-out of the telemetry feature (values `true`, `1`, or `yes` accepted); otherwise, set to `false` to opt-in to the telemetry features (values `false`, `0`, or `no` accepted).</span></span> <span data-ttu-id="45ad3-246">Jeśli nie jest ustawiony, wartości domyślne jest `false`, i funkcja telemetrii jest aktywna.</span><span class="sxs-lookup"><span data-stu-id="45ad3-246">If not set, the defaults is `false`, and the telemetry feature is active.</span></span>

---
