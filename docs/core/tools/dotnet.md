---
title: polecenie DotNet - .NET Core interfejsu wiersza polecenia
description: "Informacje o poleceniu dotnet (ogólnego sterownik narzędzi interfejsu wiersza polecenia platformy .NET Core) i jej użycia."
author: mairaw
ms.author: mairaw
ms.date: 11/28/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.workload:
- dotnetcore
ms.openlocfilehash: bed0876645428cdff11fa83a091fc63e64cedc8f
ms.sourcegitcommit: 973a12d1e6962cd9a9c263fbfaad040ec8267fe9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/22/2018
---
# <a name="dotnet-command"></a><span data-ttu-id="50e96-103">polecenie DotNet</span><span class="sxs-lookup"><span data-stu-id="50e96-103">dotnet command</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="50e96-104">Nazwa</span><span class="sxs-lookup"><span data-stu-id="50e96-104">Name</span></span>

<span data-ttu-id="50e96-105">`dotnet` -Ogólne sterownik do uruchamiania polecenia wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="50e96-105">`dotnet` - General driver for running the command-line commands.</span></span>

## <a name="synopsis"></a><span data-ttu-id="50e96-106">Streszczenie</span><span class="sxs-lookup"><span data-stu-id="50e96-106">Synopsis</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="50e96-107">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="50e96-107">.NET Core 2.x</span></span>](#tab/netcore2x)
```
dotnet [command] [arguments] [--additional-deps] [--additionalprobingpath] [-d|--diagnostics] [--fx-version] [-h|--help] [--info] [--roll-forward-on-no-candidate-fx] [-v|--verbose] [--version]
```
# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="50e96-108">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="50e96-108">.NET Core 1.x</span></span>](#tab/netcore1x)
```
dotnet [command] [arguments] [--additionalprobingpath] [-d|--diagnostics] [--fx-version] [-h|--help] [--info] [-v|--verbose] [--version]
```
---

## <a name="description"></a><span data-ttu-id="50e96-109">Opis</span><span class="sxs-lookup"><span data-stu-id="50e96-109">Description</span></span>

<span data-ttu-id="50e96-110">`dotnet` jest ogólny sterownik łańcuch narzędzi interfejsu wiersza polecenia (CLI).</span><span class="sxs-lookup"><span data-stu-id="50e96-110">`dotnet` is a generic driver for the Command Line Interface (CLI) toolchain.</span></span> <span data-ttu-id="50e96-111">Wywoływane na jego własnej, zapewnia użycia krótkie instrukcje.</span><span class="sxs-lookup"><span data-stu-id="50e96-111">Invoked on its own, it provides brief usage instructions.</span></span>

<span data-ttu-id="50e96-112">Każdej z funkcji jest implementowany jako polecenia.</span><span class="sxs-lookup"><span data-stu-id="50e96-112">Each specific feature is implemented as a command.</span></span> <span data-ttu-id="50e96-113">Aby można było użyć funkcji, polecenie określono po `dotnet`, takich jak [ `dotnet build` ](dotnet-build.md).</span><span class="sxs-lookup"><span data-stu-id="50e96-113">In order to use the feature, the command is specified after `dotnet`, such as [`dotnet build`](dotnet-build.md).</span></span> <span data-ttu-id="50e96-114">Wszystkie argumenty następujące polecenie to własną argumentów.</span><span class="sxs-lookup"><span data-stu-id="50e96-114">All of the arguments following the command are its own arguments.</span></span>

<span data-ttu-id="50e96-115">Tylko `dotnet` jest używany jako polecenia samodzielnie [aplikacje zależne od framework](../deploying/index.md).</span><span class="sxs-lookup"><span data-stu-id="50e96-115">The only time `dotnet` is used as a command on its own is to run [framework-dependent apps](../deploying/index.md).</span></span> <span data-ttu-id="50e96-116">Określ aplikację DLL po `dotnet` zlecenie do wykonywania aplikacji (na przykład `dotnet myapp.dll`).</span><span class="sxs-lookup"><span data-stu-id="50e96-116">Specify an application DLL after the `dotnet` verb to execute the application (for example, `dotnet myapp.dll`).</span></span>

## <a name="options"></a><span data-ttu-id="50e96-117">Opcje</span><span class="sxs-lookup"><span data-stu-id="50e96-117">Options</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="50e96-118">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="50e96-118">.NET Core 2.x</span></span>](#tab/netcore2x)

`--additional-deps <PATH>`

<span data-ttu-id="50e96-119">Ścieżka do dodatkowych *deps.json* pliku.</span><span class="sxs-lookup"><span data-stu-id="50e96-119">Path to additional *deps.json* file.</span></span>

`--additionalprobingpath <PATH>`

<span data-ttu-id="50e96-120">Ścieżka zawierające sondowania zasad i zestawów do sondowania.</span><span class="sxs-lookup"><span data-stu-id="50e96-120">Path containing probing policy and assemblies to probe.</span></span>

`-d|--diagnostics`

<span data-ttu-id="50e96-121">Umożliwia wyjście diagnostyczne.</span><span class="sxs-lookup"><span data-stu-id="50e96-121">Enables diagnostic output.</span></span>

`--fx-version <VERSION>`

<span data-ttu-id="50e96-122">Wersja zainstalowanego środowiska uruchomieniowego .NET Core służące do uruchamiania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="50e96-122">Version of the installed .NET Core runtime to use to run the application.</span></span>

`-h|--help`

<span data-ttu-id="50e96-123">Drukuje krótkich pomocy dla polecenia.</span><span class="sxs-lookup"><span data-stu-id="50e96-123">Prints out a short help for the command.</span></span> <span data-ttu-id="50e96-124">Jeśli używany z `dotnet`, również Wyświetla listę dostępnych poleceń.</span><span class="sxs-lookup"><span data-stu-id="50e96-124">If using with `dotnet`, it also prints a list of the available commands.</span></span>

`--info`

<span data-ttu-id="50e96-125">Drukuje szczegółowe informacje na temat narzędzi interfejsu wiersza polecenia i środowiska, takich jak bieżący system operacyjny, Zatwierdź SHA dla wersji i innych informacji.</span><span class="sxs-lookup"><span data-stu-id="50e96-125">Prints out detailed information about the CLI tooling and the environment, such as the current operating system, commit SHA for the version, and other information.</span></span>

`--roll-forward-on-no-candidate-fx`

 <span data-ttu-id="50e96-126">Przedstawia przekazywania na ma kandydata framework udostępnionego.</span><span class="sxs-lookup"><span data-stu-id="50e96-126">Rolls forward on no candidate shared framework.</span></span>

`-v|--verbose`

<span data-ttu-id="50e96-127">Włącza pełne dane wyjściowe.</span><span class="sxs-lookup"><span data-stu-id="50e96-127">Enables verbose output.</span></span>

`--version`

<span data-ttu-id="50e96-128">Drukuje wersji programu .NET Core SDK w użyciu.</span><span class="sxs-lookup"><span data-stu-id="50e96-128">Prints out the version of the .NET Core SDK in use.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="50e96-129">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="50e96-129">.NET Core 1.x</span></span>](#tab/netcore1x)

`--additionalprobingpath <PATH>`

<span data-ttu-id="50e96-130">Ścieżka zawierające sondowania zasad i zestawów do sondowania.</span><span class="sxs-lookup"><span data-stu-id="50e96-130">Path containing probing policy and assemblies to probe.</span></span>

`-d|--diagnostics`

<span data-ttu-id="50e96-131">Umożliwia wyjście diagnostyczne.</span><span class="sxs-lookup"><span data-stu-id="50e96-131">Enables diagnostic output.</span></span>

`--fx-version <VERSION>`

<span data-ttu-id="50e96-132">Wersja zainstalowanego środowiska uruchomieniowego .NET Core służące do uruchamiania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="50e96-132">Version of the installed .NET Core runtime to use to run the application.</span></span>

`-h|--help`

<span data-ttu-id="50e96-133">Drukuje krótkich pomocy dla polecenia.</span><span class="sxs-lookup"><span data-stu-id="50e96-133">Prints out a short help for the command.</span></span> <span data-ttu-id="50e96-134">Jeśli używany z `dotnet`, również Wyświetla listę dostępnych poleceń.</span><span class="sxs-lookup"><span data-stu-id="50e96-134">If using with `dotnet`, it also prints a list of the available commands.</span></span>

`--info`

<span data-ttu-id="50e96-135">Drukuje szczegółowe informacje na temat narzędzi interfejsu wiersza polecenia i środowiska, takich jak bieżący system operacyjny, Zatwierdź SHA dla wersji i innych informacji.</span><span class="sxs-lookup"><span data-stu-id="50e96-135">Prints out detailed information about the CLI tooling and the environment, such as the current operating system, commit SHA for the version, and other information.</span></span>

`-v|--verbose`

<span data-ttu-id="50e96-136">Włącza pełne dane wyjściowe.</span><span class="sxs-lookup"><span data-stu-id="50e96-136">Enables verbose output.</span></span>

`--version`

<span data-ttu-id="50e96-137">Drukuje wersji programu .NET Core SDK w użyciu.</span><span class="sxs-lookup"><span data-stu-id="50e96-137">Prints out the version of the .NET Core SDK in use.</span></span>

---

## <a name="dotnet-commands"></a><span data-ttu-id="50e96-138">polecenia DotNet</span><span class="sxs-lookup"><span data-stu-id="50e96-138">dotnet commands</span></span>

### <a name="general"></a><span data-ttu-id="50e96-139">Ogólne</span><span class="sxs-lookup"><span data-stu-id="50e96-139">General</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="50e96-140">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="50e96-140">.NET Core 2.x</span></span>](#tab/netcore2x)

| <span data-ttu-id="50e96-141">Polecenie</span><span class="sxs-lookup"><span data-stu-id="50e96-141">Command</span></span>                             | <span data-ttu-id="50e96-142">Funkcja</span><span class="sxs-lookup"><span data-stu-id="50e96-142">Function</span></span>                                                            |
| ----------------------------------- | ------------------------------------------------------------------- |
| [<span data-ttu-id="50e96-143">dotnet build</span><span class="sxs-lookup"><span data-stu-id="50e96-143">dotnet build</span></span>](dotnet-build.md)     | <span data-ttu-id="50e96-144">Tworzy aplikacji .NET Core.</span><span class="sxs-lookup"><span data-stu-id="50e96-144">Builds a .NET Core application.</span></span>                                     |
| [<span data-ttu-id="50e96-145">dotnet clean</span><span class="sxs-lookup"><span data-stu-id="50e96-145">dotnet clean</span></span>](dotnet-clean.md)     | <span data-ttu-id="50e96-146">Wyczyść wyniki do kompilacji.</span><span class="sxs-lookup"><span data-stu-id="50e96-146">Clean build outputs.</span></span>                                              |
| [<span data-ttu-id="50e96-147">dotnet help</span><span class="sxs-lookup"><span data-stu-id="50e96-147">dotnet help</span></span>](dotnet-help.md)       | <span data-ttu-id="50e96-148">Przedstawia szczegółowe dokumentacji online dla polecenia.</span><span class="sxs-lookup"><span data-stu-id="50e96-148">Shows more detailed documentation online for the command.</span></span>           |
| [<span data-ttu-id="50e96-149">dotnet migrate</span><span class="sxs-lookup"><span data-stu-id="50e96-149">dotnet migrate</span></span>](dotnet-migrate.md) | <span data-ttu-id="50e96-150">Wykonuje migrację prawidłowy projekt Preview 2 projektu .NET Core SDK 1.0.</span><span class="sxs-lookup"><span data-stu-id="50e96-150">Migrates a valid Preview 2 project to a .NET Core SDK 1.0 project.</span></span>  |
| [<span data-ttu-id="50e96-151">dotnet msbuild</span><span class="sxs-lookup"><span data-stu-id="50e96-151">dotnet msbuild</span></span>](dotnet-msbuild.md) | <span data-ttu-id="50e96-152">Zapewnia dostęp do wiersza polecenia programu MSBuild.</span><span class="sxs-lookup"><span data-stu-id="50e96-152">Provides access to the MSBuild command line.</span></span>                        |
| [<span data-ttu-id="50e96-153">dotnet new</span><span class="sxs-lookup"><span data-stu-id="50e96-153">dotnet new</span></span>](dotnet-new.md)         | <span data-ttu-id="50e96-154">Inicjuje języka C# lub projektów F # dla danego szablonu.</span><span class="sxs-lookup"><span data-stu-id="50e96-154">Initializes a C# or F# project for a given template.</span></span>                |
| [<span data-ttu-id="50e96-155">dotnet pack</span><span class="sxs-lookup"><span data-stu-id="50e96-155">dotnet pack</span></span>](dotnet-pack.md)       | <span data-ttu-id="50e96-156">Tworzy pakiet NuGet kodu.</span><span class="sxs-lookup"><span data-stu-id="50e96-156">Creates a NuGet package of your code.</span></span>                               |
| [<span data-ttu-id="50e96-157">dotnet publish</span><span class="sxs-lookup"><span data-stu-id="50e96-157">dotnet publish</span></span>](dotnet-publish.md) | <span data-ttu-id="50e96-158">Publikowanie aplikacji .NET framework zależne lub niezależne.</span><span class="sxs-lookup"><span data-stu-id="50e96-158">Publishes a .NET framework-dependent or self-contained application.</span></span> |
| [<span data-ttu-id="50e96-159">dotnet restore</span><span class="sxs-lookup"><span data-stu-id="50e96-159">dotnet restore</span></span>](dotnet-restore.md) | <span data-ttu-id="50e96-160">Przywraca zależności dla danej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="50e96-160">Restores the dependencies for a given application.</span></span>                  |
| [<span data-ttu-id="50e96-161">dotnet run</span><span class="sxs-lookup"><span data-stu-id="50e96-161">dotnet run</span></span>](dotnet-run.md)         | <span data-ttu-id="50e96-162">Aplikacja jest uruchamiana ze źródła.</span><span class="sxs-lookup"><span data-stu-id="50e96-162">Runs the application from source.</span></span>                                   |
| [<span data-ttu-id="50e96-163">dotnet sln</span><span class="sxs-lookup"><span data-stu-id="50e96-163">dotnet sln</span></span>](dotnet-sln.md)         | <span data-ttu-id="50e96-164">Opcje do dodawania, usuwania i wyświetlić listę projektów w pliku rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="50e96-164">Options to add, remove, and list projects in a solution file.</span></span>       |
| [<span data-ttu-id="50e96-165">dotnet store</span><span class="sxs-lookup"><span data-stu-id="50e96-165">dotnet store</span></span>](dotnet-store.md)     | <span data-ttu-id="50e96-166">Przechowuje zestawy w magazynie pakietów środowiska wykonawczego.</span><span class="sxs-lookup"><span data-stu-id="50e96-166">Stores assemblies in the runtime package store.</span></span>                     |
| [<span data-ttu-id="50e96-167">dotnet test</span><span class="sxs-lookup"><span data-stu-id="50e96-167">dotnet test</span></span>](dotnet-test.md)       | <span data-ttu-id="50e96-168">Uruchamia testy przy użyciu runner testu.</span><span class="sxs-lookup"><span data-stu-id="50e96-168">Runs tests using a test runner.</span></span>                                     |

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="50e96-169">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="50e96-169">.NET Core 1.x</span></span>](#tab/netcore1x)

| <span data-ttu-id="50e96-170">Polecenie</span><span class="sxs-lookup"><span data-stu-id="50e96-170">Command</span></span>                             | <span data-ttu-id="50e96-171">Funkcja</span><span class="sxs-lookup"><span data-stu-id="50e96-171">Function</span></span>                                                            |
| ----------------------------------- | ------------------------------------------------------------------- |
| [<span data-ttu-id="50e96-172">dotnet build</span><span class="sxs-lookup"><span data-stu-id="50e96-172">dotnet build</span></span>](dotnet-build.md)     | <span data-ttu-id="50e96-173">Tworzy aplikacji .NET Core.</span><span class="sxs-lookup"><span data-stu-id="50e96-173">Builds a .NET Core application.</span></span>                                     |
| [<span data-ttu-id="50e96-174">dotnet clean</span><span class="sxs-lookup"><span data-stu-id="50e96-174">dotnet clean</span></span>](dotnet-clean.md)     | <span data-ttu-id="50e96-175">Wyczyść wyniki do kompilacji.</span><span class="sxs-lookup"><span data-stu-id="50e96-175">Clean build outputs.</span></span>                                              |
| [<span data-ttu-id="50e96-176">dotnet migrate</span><span class="sxs-lookup"><span data-stu-id="50e96-176">dotnet migrate</span></span>](dotnet-migrate.md) | <span data-ttu-id="50e96-177">Wykonuje migrację prawidłowy projekt Preview 2 projektu .NET Core SDK 1.0.</span><span class="sxs-lookup"><span data-stu-id="50e96-177">Migrates a valid Preview 2 project to a .NET Core SDK 1.0 project.</span></span>  |
| [<span data-ttu-id="50e96-178">dotnet msbuild</span><span class="sxs-lookup"><span data-stu-id="50e96-178">dotnet msbuild</span></span>](dotnet-msbuild.md) | <span data-ttu-id="50e96-179">Zapewnia dostęp do wiersza polecenia programu MSBuild.</span><span class="sxs-lookup"><span data-stu-id="50e96-179">Provides access to the MSBuild command line.</span></span>                        |
| [<span data-ttu-id="50e96-180">dotnet new</span><span class="sxs-lookup"><span data-stu-id="50e96-180">dotnet new</span></span>](dotnet-new.md)         | <span data-ttu-id="50e96-181">Inicjuje języka C# lub projektów F # dla danego szablonu.</span><span class="sxs-lookup"><span data-stu-id="50e96-181">Initializes a C# or F# project for a given template.</span></span>                |
| [<span data-ttu-id="50e96-182">dotnet pack</span><span class="sxs-lookup"><span data-stu-id="50e96-182">dotnet pack</span></span>](dotnet-pack.md)       | <span data-ttu-id="50e96-183">Tworzy pakiet NuGet kodu.</span><span class="sxs-lookup"><span data-stu-id="50e96-183">Creates a NuGet package of your code.</span></span>                               |
| [<span data-ttu-id="50e96-184">dotnet publish</span><span class="sxs-lookup"><span data-stu-id="50e96-184">dotnet publish</span></span>](dotnet-publish.md) | <span data-ttu-id="50e96-185">Publikowanie aplikacji .NET framework zależne lub niezależne.</span><span class="sxs-lookup"><span data-stu-id="50e96-185">Publishes a .NET framework-dependent or self-contained application.</span></span> |
| [<span data-ttu-id="50e96-186">dotnet restore</span><span class="sxs-lookup"><span data-stu-id="50e96-186">dotnet restore</span></span>](dotnet-restore.md) | <span data-ttu-id="50e96-187">Przywraca zależności dla danej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="50e96-187">Restores the dependencies for a given application.</span></span>                  |
| [<span data-ttu-id="50e96-188">dotnet run</span><span class="sxs-lookup"><span data-stu-id="50e96-188">dotnet run</span></span>](dotnet-run.md)         | <span data-ttu-id="50e96-189">Aplikacja jest uruchamiana ze źródła.</span><span class="sxs-lookup"><span data-stu-id="50e96-189">Runs the application from source.</span></span>                                   |
| [<span data-ttu-id="50e96-190">dotnet sln</span><span class="sxs-lookup"><span data-stu-id="50e96-190">dotnet sln</span></span>](dotnet-sln.md)         | <span data-ttu-id="50e96-191">Opcje do dodawania, usuwania i wyświetlić listę projektów w pliku rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="50e96-191">Options to add, remove, and list projects in a solution file.</span></span>       |
| [<span data-ttu-id="50e96-192">dotnet test</span><span class="sxs-lookup"><span data-stu-id="50e96-192">dotnet test</span></span>](dotnet-test.md)       | <span data-ttu-id="50e96-193">Uruchamia testy przy użyciu runner testu.</span><span class="sxs-lookup"><span data-stu-id="50e96-193">Runs tests using a test runner.</span></span>                                     |

---

### <a name="project-references"></a><span data-ttu-id="50e96-194">Odwołania do projektu</span><span class="sxs-lookup"><span data-stu-id="50e96-194">Project references</span></span>

<span data-ttu-id="50e96-195">Polecenie</span><span class="sxs-lookup"><span data-stu-id="50e96-195">Command</span></span> | <span data-ttu-id="50e96-196">Funkcja</span><span class="sxs-lookup"><span data-stu-id="50e96-196">Function</span></span>
--- | ---
[<span data-ttu-id="50e96-197">dotnet add reference</span><span class="sxs-lookup"><span data-stu-id="50e96-197">dotnet add reference</span></span>](dotnet-add-reference.md) | <span data-ttu-id="50e96-198">Dodaj odwołanie do projektu.</span><span class="sxs-lookup"><span data-stu-id="50e96-198">Add a project reference.</span></span>
[<span data-ttu-id="50e96-199">dotnet list reference</span><span class="sxs-lookup"><span data-stu-id="50e96-199">dotnet list reference</span></span>](dotnet-list-reference.md) | <span data-ttu-id="50e96-200">Lista odwołań do projektu.</span><span class="sxs-lookup"><span data-stu-id="50e96-200">List project references.</span></span>
[<span data-ttu-id="50e96-201">dotnet remove reference</span><span class="sxs-lookup"><span data-stu-id="50e96-201">dotnet remove reference</span></span>](dotnet-remove-reference.md) | <span data-ttu-id="50e96-202">Usuń odwołanie do projektu.</span><span class="sxs-lookup"><span data-stu-id="50e96-202">Remove a project reference.</span></span>

### <a name="nuget-packages"></a><span data-ttu-id="50e96-203">Pakiety NuGet</span><span class="sxs-lookup"><span data-stu-id="50e96-203">NuGet packages</span></span>

<span data-ttu-id="50e96-204">Polecenie</span><span class="sxs-lookup"><span data-stu-id="50e96-204">Command</span></span> | <span data-ttu-id="50e96-205">Funkcja</span><span class="sxs-lookup"><span data-stu-id="50e96-205">Function</span></span>
--- | ---
[<span data-ttu-id="50e96-206">dotnet add package</span><span class="sxs-lookup"><span data-stu-id="50e96-206">dotnet add package</span></span>](dotnet-add-package.md) | <span data-ttu-id="50e96-207">Dodaj pakiet NuGet.</span><span class="sxs-lookup"><span data-stu-id="50e96-207">Add a NuGet package.</span></span>
[<span data-ttu-id="50e96-208">dotnet remove package</span><span class="sxs-lookup"><span data-stu-id="50e96-208">dotnet remove package</span></span>](dotnet-remove-package.md) | <span data-ttu-id="50e96-209">Usunięcie pakietu NuGet.</span><span class="sxs-lookup"><span data-stu-id="50e96-209">Remove a NuGet package.</span></span>

### <a name="nuget-commands"></a><span data-ttu-id="50e96-210">Polecenia NuGet</span><span class="sxs-lookup"><span data-stu-id="50e96-210">NuGet commands</span></span>

<span data-ttu-id="50e96-211">Polecenie</span><span class="sxs-lookup"><span data-stu-id="50e96-211">Command</span></span> | <span data-ttu-id="50e96-212">Funkcja</span><span class="sxs-lookup"><span data-stu-id="50e96-212">Function</span></span>
--- | ---
[<span data-ttu-id="50e96-213">dotnet nuget delete</span><span class="sxs-lookup"><span data-stu-id="50e96-213">dotnet nuget delete</span></span>](dotnet-nuget-delete.md) | <span data-ttu-id="50e96-214">Usuwa lub unlists pakietu z serwera.</span><span class="sxs-lookup"><span data-stu-id="50e96-214">Deletes or unlists a package from the server.</span></span>
[<span data-ttu-id="50e96-215">dotnet nuget locals</span><span class="sxs-lookup"><span data-stu-id="50e96-215">dotnet nuget locals</span></span>](dotnet-nuget-locals.md) | <span data-ttu-id="50e96-216">Czyści lub wyświetla ich listę zasobów lokalnych NuGet np. pamięci podręcznej żądania http, tymczasowego pamięci podręcznej lub folderu packages globalne dla komputera.</span><span class="sxs-lookup"><span data-stu-id="50e96-216">Clears or lists local NuGet resources such as http-request cache, temporary cache, or machine-wide global packages folder.</span></span>
[<span data-ttu-id="50e96-217">dotnet nuget push</span><span class="sxs-lookup"><span data-stu-id="50e96-217">dotnet nuget push</span></span>](dotnet-nuget-push.md) | <span data-ttu-id="50e96-218">Wypychanie pakietu do serwera i publikuje ją.</span><span class="sxs-lookup"><span data-stu-id="50e96-218">Pushes a package to the server and publishes it.</span></span>

## <a name="examples"></a><span data-ttu-id="50e96-219">Przykłady</span><span class="sxs-lookup"><span data-stu-id="50e96-219">Examples</span></span>

<span data-ttu-id="50e96-220">Inicjowanie przykładowej aplikacji konsoli .NET Core, który można skompilować i uruchomić:</span><span class="sxs-lookup"><span data-stu-id="50e96-220">Initialize a sample .NET Core console application that can be compiled and run:</span></span>

`dotnet new console`

<span data-ttu-id="50e96-221">Przywróć zależności dla danej aplikacji:</span><span class="sxs-lookup"><span data-stu-id="50e96-221">Restore dependencies for a given application:</span></span>

`dotnet restore`

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

<span data-ttu-id="50e96-222">Tworzenie projektu i jego zależności w podanym katalogu:</span><span class="sxs-lookup"><span data-stu-id="50e96-222">Build a project and its dependencies in a given directory:</span></span>

`dotnet build`

<span data-ttu-id="50e96-223">Uruchamianie aplikacji zależnych od framework o nazwie `myapp.dll`:</span><span class="sxs-lookup"><span data-stu-id="50e96-223">Run a framework-dependent app named `myapp.dll`:</span></span>

`dotnet myapp.dll`

## <a name="environment-variables"></a><span data-ttu-id="50e96-224">Zmienne środowiskowe</span><span class="sxs-lookup"><span data-stu-id="50e96-224">Environment variables</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="50e96-225">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="50e96-225">.NET Core 2.x</span></span>](#tab/netcore2x)

`DOTNET_PACKAGES`

<span data-ttu-id="50e96-226">Pakiet główny pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="50e96-226">The primary package cache.</span></span> <span data-ttu-id="50e96-227">Jeśli nie został ustawiony, domyślnie `$HOME/.nuget/packages` w systemie Unix lub `%HOME%\NuGet\Packages` w systemie Windows.</span><span class="sxs-lookup"><span data-stu-id="50e96-227">If not set, it defaults to `$HOME/.nuget/packages` on Unix or `%HOME%\NuGet\Packages` on Windows.</span></span>

`DOTNET_SERVICING`

<span data-ttu-id="50e96-228">Określa lokalizację obsługi indeksu jest używany przez hosta udostępnionych podczas ładowania środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="50e96-228">Specifies the location of the servicing index to use by the shared host when loading the runtime.</span></span>

`DOTNET_CLI_TELEMETRY_OPTOUT`

<span data-ttu-id="50e96-229">Określa, czy dane dotyczące użycia narzędzia .NET Core został zebrany i wysyłany do firmy Microsoft.</span><span class="sxs-lookup"><span data-stu-id="50e96-229">Specifies whether data about the .NET Core tools usage is collected and sent to Microsoft.</span></span> <span data-ttu-id="50e96-230">Ustaw `true` Aby zrezygnować z funkcji telemetrii (wartości `true`, `1`, lub `yes` zaakceptowane), w przeciwnym razie należy ustawić `false` w funkcji telemetrii (wartości `false`, `0`, lub `no` akceptowane).</span><span class="sxs-lookup"><span data-stu-id="50e96-230">Set to `true` to opt-out of the telemetry feature (values `true`, `1`, or `yes` accepted); otherwise, set to `false` to opt-in to the telemetry features (values `false`, `0`, or `no` accepted).</span></span> <span data-ttu-id="50e96-231">Jeśli nie jest ustawiony, wartości domyślne jest `false`, i funkcja telemetrii jest aktywna.</span><span class="sxs-lookup"><span data-stu-id="50e96-231">If not set, the defaults is `false`, and the telemetry feature is active.</span></span>

`DOTNET_MULTILEVEL_LOOKUP`

<span data-ttu-id="50e96-232">Określa, czy podstawowego środowiska wykonawczego .NET, udostępnionych framework lub zestawu SDK są rozpoznane w globalnej lokalizacji.</span><span class="sxs-lookup"><span data-stu-id="50e96-232">Specifies whether .NET Core runtime, shared framework or SDK are resolved from the global location.</span></span> <span data-ttu-id="50e96-233">Jeśli nie jest ustawiona, domyślne `true`.</span><span class="sxs-lookup"><span data-stu-id="50e96-233">If not set, it defaults to `true`.</span></span> <span data-ttu-id="50e96-234">Ustaw `false` rozwiązania z globalnej lokalizacji i mają odizolowane instalacji platformy .NET Core (wartości `0` lub `false` są akceptowane).</span><span class="sxs-lookup"><span data-stu-id="50e96-234">Set to `false` to not resolve from the global location and have isolated .NET Core installations (values `0` or `false` are accepted).</span></span> <span data-ttu-id="50e96-235">Aby uzyskać więcej informacji na temat wyszukiwania wielopoziomowe zobacz [wyszukiwania SharedFX wielopoziomowej](https://github.com/dotnet/core-setup/blob/master/Documentation/design-docs/multilevel-sharedfx-lookup.md).</span><span class="sxs-lookup"><span data-stu-id="50e96-235">For more information about multi-level lookup, see [Multi-level SharedFX Lookup](https://github.com/dotnet/core-setup/blob/master/Documentation/design-docs/multilevel-sharedfx-lookup.md).</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="50e96-236">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="50e96-236">.NET Core 1.x</span></span>](#tab/netcore1x)

`DOTNET_PACKAGES`

<span data-ttu-id="50e96-237">Pakiet główny pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="50e96-237">The primary package cache.</span></span> <span data-ttu-id="50e96-238">Jeśli nie został ustawiony, domyślnie `$HOME/.nuget/packages` w systemie Unix lub `%HOME%\NuGet\Packages` w systemie Windows.</span><span class="sxs-lookup"><span data-stu-id="50e96-238">If not set, it defaults to `$HOME/.nuget/packages` on Unix or `%HOME%\NuGet\Packages` on Windows.</span></span>

`DOTNET_SERVICING`

<span data-ttu-id="50e96-239">Określa lokalizację obsługi indeksu jest używany przez hosta udostępnionych podczas ładowania środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="50e96-239">Specifies the location of the servicing index to use by the shared host when loading the runtime.</span></span>

`DOTNET_CLI_TELEMETRY_OPTOUT`

<span data-ttu-id="50e96-240">Określa, czy dane dotyczące użycia narzędzia .NET Core został zebrany i wysyłany do firmy Microsoft.</span><span class="sxs-lookup"><span data-stu-id="50e96-240">Specifies whether data about the .NET Core tools usage is collected and sent to Microsoft.</span></span> <span data-ttu-id="50e96-241">Ustaw `true` Aby zrezygnować z funkcji telemetrii (wartości `true`, `1`, lub `yes` zaakceptowane), w przeciwnym razie należy ustawić `false` w funkcji telemetrii (wartości `false`, `0`, lub `no` akceptowane).</span><span class="sxs-lookup"><span data-stu-id="50e96-241">Set to `true` to opt-out of the telemetry feature (values `true`, `1`, or `yes` accepted); otherwise, set to `false` to opt-in to the telemetry features (values `false`, `0`, or `no` accepted).</span></span> <span data-ttu-id="50e96-242">Jeśli nie jest ustawiony, wartości domyślne jest `false`, i funkcja telemetrii jest aktywna.</span><span class="sxs-lookup"><span data-stu-id="50e96-242">If not set, the defaults is `false`, and the telemetry feature is active.</span></span>

---
