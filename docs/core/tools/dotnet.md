---
title: polecenie DotNet - .NET Core interfejsu wiersza polecenia
description: "Informacje o poleceniu dotnet (ogólnego sterownik narzędzi interfejsu wiersza polecenia platformy .NET Core) i jej użycia."
author: mairaw
ms.author: mairaw
ms.date: 08/14/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.workload:
- dotnetcore
ms.openlocfilehash: 2eea7d13994bfddc89d8f3513308a6620c53c88c
ms.sourcegitcommit: f28752eab00d2bd97e971542c0f49ce63cfbc239
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/29/2018
---
# <a name="dotnet-command"></a><span data-ttu-id="8c3b7-103">polecenie DotNet</span><span class="sxs-lookup"><span data-stu-id="8c3b7-103">dotnet command</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="8c3b7-104">Nazwa</span><span class="sxs-lookup"><span data-stu-id="8c3b7-104">Name</span></span>

<span data-ttu-id="8c3b7-105">`dotnet`-Ogólne sterownik do uruchamiania polecenia wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="8c3b7-105">`dotnet` - General driver for running the command-line commands.</span></span>

## <a name="synopsis"></a><span data-ttu-id="8c3b7-106">Streszczenie</span><span class="sxs-lookup"><span data-stu-id="8c3b7-106">Synopsis</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="8c3b7-107">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="8c3b7-107">.NET Core 2.x</span></span>](#tab/netcore2x)
```
dotnet [command] [arguments] [--additional-deps] [--additionalprobingpath] [-d|--diagnostics] [--fx-version] [-h|--help] [--info] [--roll-forward-on-no-candidate-fx] [-v|--verbose] [--version]
```
# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="8c3b7-108">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="8c3b7-108">.NET Core 1.x</span></span>](#tab/netcore1x)
```
dotnet [command] [arguments] [--additionalprobingpath] [-d|--diagnostics] [--fx-version] [-h|--help] [--info] [-v|--verbose] [--version]
```
---

## <a name="description"></a><span data-ttu-id="8c3b7-109">Opis</span><span class="sxs-lookup"><span data-stu-id="8c3b7-109">Description</span></span>

<span data-ttu-id="8c3b7-110">`dotnet`jest ogólny sterownik łańcuch narzędzi interfejsu wiersza polecenia (CLI).</span><span class="sxs-lookup"><span data-stu-id="8c3b7-110">`dotnet` is a generic driver for the Command Line Interface (CLI) toolchain.</span></span> <span data-ttu-id="8c3b7-111">Wywoływane na jego własnej, zapewnia użycia krótkie instrukcje.</span><span class="sxs-lookup"><span data-stu-id="8c3b7-111">Invoked on its own, it provides brief usage instructions.</span></span>

<span data-ttu-id="8c3b7-112">Każdej z funkcji jest implementowany jako polecenia.</span><span class="sxs-lookup"><span data-stu-id="8c3b7-112">Each specific feature is implemented as a command.</span></span> <span data-ttu-id="8c3b7-113">Aby można było użyć funkcji, polecenie określono po `dotnet`, takich jak [ `dotnet build` ](dotnet-build.md).</span><span class="sxs-lookup"><span data-stu-id="8c3b7-113">In order to use the feature, the command is specified after `dotnet`, such as [`dotnet build`](dotnet-build.md).</span></span> <span data-ttu-id="8c3b7-114">Wszystkie argumenty następujące polecenie to własną argumentów.</span><span class="sxs-lookup"><span data-stu-id="8c3b7-114">All of the arguments following the command are its own arguments.</span></span>

<span data-ttu-id="8c3b7-115">Tylko `dotnet` jest używany jako polecenia samodzielnie [aplikacje zależne od framework](../deploying/index.md).</span><span class="sxs-lookup"><span data-stu-id="8c3b7-115">The only time `dotnet` is used as a command on its own is to run [framework-dependent apps](../deploying/index.md).</span></span> <span data-ttu-id="8c3b7-116">Określ aplikację DLL po `dotnet` zlecenie do wykonywania aplikacji (na przykład `dotnet myapp.dll`).</span><span class="sxs-lookup"><span data-stu-id="8c3b7-116">Specify an application DLL after the `dotnet` verb to execute the application (for example, `dotnet myapp.dll`).</span></span>

## <a name="options"></a><span data-ttu-id="8c3b7-117">Opcje</span><span class="sxs-lookup"><span data-stu-id="8c3b7-117">Options</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="8c3b7-118">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="8c3b7-118">.NET Core 2.x</span></span>](#tab/netcore2x)

`--additional-deps <PATH>`

<span data-ttu-id="8c3b7-119">Ścieżka do dodatkowych *deps.json* pliku.</span><span class="sxs-lookup"><span data-stu-id="8c3b7-119">Path to additional *deps.json* file.</span></span>

`--additionalprobingpath <PATH>`

<span data-ttu-id="8c3b7-120">Ścieżka zawierające sondowania zasad i zestawów do sondowania.</span><span class="sxs-lookup"><span data-stu-id="8c3b7-120">Path containing probing policy and assemblies to probe.</span></span>

`-d|--diagnostics`

<span data-ttu-id="8c3b7-121">Umożliwia wyjście diagnostyczne.</span><span class="sxs-lookup"><span data-stu-id="8c3b7-121">Enables diagnostic output.</span></span>

`--fx-version <VERSION>`

<span data-ttu-id="8c3b7-122">Wersja zainstalowanego środowiska uruchomieniowego .NET Core służące do uruchamiania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="8c3b7-122">Version of the installed .NET Core runtime to use to run the application.</span></span>

`-h|--help`

<span data-ttu-id="8c3b7-123">Drukuje krótkich pomocy dla polecenia.</span><span class="sxs-lookup"><span data-stu-id="8c3b7-123">Prints out a short help for the command.</span></span> <span data-ttu-id="8c3b7-124">Jeśli używany z `dotnet`, również Wyświetla listę dostępnych poleceń.</span><span class="sxs-lookup"><span data-stu-id="8c3b7-124">If using with `dotnet`, it also prints a list of the available commands.</span></span>

`--info`

<span data-ttu-id="8c3b7-125">Drukuje szczegółowe informacje na temat narzędzi interfejsu wiersza polecenia i środowiska, takich jak bieżący system operacyjny, Zatwierdź SHA dla wersji i innych informacji.</span><span class="sxs-lookup"><span data-stu-id="8c3b7-125">Prints out detailed information about the CLI tooling and the environment, such as the current operating system, commit SHA for the version, and other information.</span></span>

`--roll-forward-on-no-candidate-fx`

 <span data-ttu-id="8c3b7-126">Przedstawia przekazywania na ma kandydata framework udostępnionego.</span><span class="sxs-lookup"><span data-stu-id="8c3b7-126">Rolls forward on no candidate shared framework.</span></span>

`-v|--verbose`

<span data-ttu-id="8c3b7-127">Włącza pełne dane wyjściowe.</span><span class="sxs-lookup"><span data-stu-id="8c3b7-127">Enables verbose output.</span></span>

`--version`

<span data-ttu-id="8c3b7-128">Drukuje wersji programu .NET Core SDK w użyciu.</span><span class="sxs-lookup"><span data-stu-id="8c3b7-128">Prints out the version of the .NET Core SDK in use.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="8c3b7-129">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="8c3b7-129">.NET Core 1.x</span></span>](#tab/netcore1x)

`--additionalprobingpath <PATH>`

<span data-ttu-id="8c3b7-130">Ścieżka zawierające sondowania zasad i zestawów do sondowania.</span><span class="sxs-lookup"><span data-stu-id="8c3b7-130">Path containing probing policy and assemblies to probe.</span></span>

`-d|--diagnostics`

<span data-ttu-id="8c3b7-131">Umożliwia wyjście diagnostyczne.</span><span class="sxs-lookup"><span data-stu-id="8c3b7-131">Enables diagnostic output.</span></span>

`--fx-version <VERSION>`

<span data-ttu-id="8c3b7-132">Wersja zainstalowanego środowiska uruchomieniowego .NET Core służące do uruchamiania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="8c3b7-132">Version of the installed .NET Core runtime to use to run the application.</span></span>

`-h|--help`

<span data-ttu-id="8c3b7-133">Drukuje krótkich pomocy dla polecenia.</span><span class="sxs-lookup"><span data-stu-id="8c3b7-133">Prints out a short help for the command.</span></span> <span data-ttu-id="8c3b7-134">Jeśli używany z `dotnet`, również Wyświetla listę dostępnych poleceń.</span><span class="sxs-lookup"><span data-stu-id="8c3b7-134">If using with `dotnet`, it also prints a list of the available commands.</span></span>

`--info`

<span data-ttu-id="8c3b7-135">Drukuje szczegółowe informacje na temat narzędzi interfejsu wiersza polecenia i środowiska, takich jak bieżący system operacyjny, Zatwierdź SHA dla wersji i innych informacji.</span><span class="sxs-lookup"><span data-stu-id="8c3b7-135">Prints out detailed information about the CLI tooling and the environment, such as the current operating system, commit SHA for the version, and other information.</span></span>

`-v|--verbose`

<span data-ttu-id="8c3b7-136">Włącza pełne dane wyjściowe.</span><span class="sxs-lookup"><span data-stu-id="8c3b7-136">Enables verbose output.</span></span>

`--version`

<span data-ttu-id="8c3b7-137">Drukuje wersji programu .NET Core SDK w użyciu.</span><span class="sxs-lookup"><span data-stu-id="8c3b7-137">Prints out the version of the .NET Core SDK in use.</span></span>

---

## <a name="dotnet-commands"></a><span data-ttu-id="8c3b7-138">polecenia DotNet</span><span class="sxs-lookup"><span data-stu-id="8c3b7-138">dotnet commands</span></span>

### <a name="general"></a><span data-ttu-id="8c3b7-139">Ogólne</span><span class="sxs-lookup"><span data-stu-id="8c3b7-139">General</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="8c3b7-140">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="8c3b7-140">.NET Core 2.x</span></span>](#tab/netcore2x)

| <span data-ttu-id="8c3b7-141">Polecenie</span><span class="sxs-lookup"><span data-stu-id="8c3b7-141">Command</span></span>                             | <span data-ttu-id="8c3b7-142">Funkcja</span><span class="sxs-lookup"><span data-stu-id="8c3b7-142">Function</span></span>                                                            |
| ----------------------------------- | ------------------------------------------------------------------- |
| [<span data-ttu-id="8c3b7-143">dotnet build</span><span class="sxs-lookup"><span data-stu-id="8c3b7-143">dotnet build</span></span>](dotnet-build.md)     | <span data-ttu-id="8c3b7-144">Tworzy aplikacji .NET Core.</span><span class="sxs-lookup"><span data-stu-id="8c3b7-144">Builds a .NET Core application.</span></span>                                     |
| [<span data-ttu-id="8c3b7-145">dotnet clean</span><span class="sxs-lookup"><span data-stu-id="8c3b7-145">dotnet clean</span></span>](dotnet-clean.md)     | <span data-ttu-id="8c3b7-146">Wyczyść wyniki do kompilacji.</span><span class="sxs-lookup"><span data-stu-id="8c3b7-146">Clean build outputs.</span></span>                                              |
| [<span data-ttu-id="8c3b7-147">dotnet help</span><span class="sxs-lookup"><span data-stu-id="8c3b7-147">dotnet help</span></span>](dotnet-help.md)       | <span data-ttu-id="8c3b7-148">Przedstawia szczegółowe dokumentacji online dla polecenia.</span><span class="sxs-lookup"><span data-stu-id="8c3b7-148">Shows more detailed documentation online for the command.</span></span>           |
| [<span data-ttu-id="8c3b7-149">dotnet migrate</span><span class="sxs-lookup"><span data-stu-id="8c3b7-149">dotnet migrate</span></span>](dotnet-migrate.md) | <span data-ttu-id="8c3b7-150">Wykonuje migrację prawidłowy projekt Preview 2 projektu .NET Core SDK 1.0.</span><span class="sxs-lookup"><span data-stu-id="8c3b7-150">Migrates a valid Preview 2 project to a .NET Core SDK 1.0 project.</span></span>  |
| [<span data-ttu-id="8c3b7-151">dotnet msbuild</span><span class="sxs-lookup"><span data-stu-id="8c3b7-151">dotnet msbuild</span></span>](dotnet-msbuild.md) | <span data-ttu-id="8c3b7-152">Zapewnia dostęp do wiersza polecenia programu MSBuild.</span><span class="sxs-lookup"><span data-stu-id="8c3b7-152">Provides access to the MSBuild command line.</span></span>                        |
| [<span data-ttu-id="8c3b7-153">dotnet new</span><span class="sxs-lookup"><span data-stu-id="8c3b7-153">dotnet new</span></span>](dotnet-new.md)         | <span data-ttu-id="8c3b7-154">Inicjuje języka C# lub projektów F # dla danego szablonu.</span><span class="sxs-lookup"><span data-stu-id="8c3b7-154">Initializes a C# or F# project for a given template.</span></span>                |
| [<span data-ttu-id="8c3b7-155">dotnet pack</span><span class="sxs-lookup"><span data-stu-id="8c3b7-155">dotnet pack</span></span>](dotnet-pack.md)       | <span data-ttu-id="8c3b7-156">Tworzy pakiet NuGet kodu.</span><span class="sxs-lookup"><span data-stu-id="8c3b7-156">Creates a NuGet package of your code.</span></span>                               |
| [<span data-ttu-id="8c3b7-157">dotnet publish</span><span class="sxs-lookup"><span data-stu-id="8c3b7-157">dotnet publish</span></span>](dotnet-publish.md) | <span data-ttu-id="8c3b7-158">Publikowanie aplikacji .NET framework zależne lub niezależne.</span><span class="sxs-lookup"><span data-stu-id="8c3b7-158">Publishes a .NET framework-dependent or self-contained application.</span></span> |
| [<span data-ttu-id="8c3b7-159">dotnet restore</span><span class="sxs-lookup"><span data-stu-id="8c3b7-159">dotnet restore</span></span>](dotnet-restore.md) | <span data-ttu-id="8c3b7-160">Przywraca zależności dla danej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="8c3b7-160">Restores the dependencies for a given application.</span></span>                  |
| [<span data-ttu-id="8c3b7-161">dotnet run</span><span class="sxs-lookup"><span data-stu-id="8c3b7-161">dotnet run</span></span>](dotnet-run.md)         | <span data-ttu-id="8c3b7-162">Aplikacja jest uruchamiana ze źródła.</span><span class="sxs-lookup"><span data-stu-id="8c3b7-162">Runs the application from source.</span></span>                                   |
| [<span data-ttu-id="8c3b7-163">dotnet sln</span><span class="sxs-lookup"><span data-stu-id="8c3b7-163">dotnet sln</span></span>](dotnet-sln.md)         | <span data-ttu-id="8c3b7-164">Opcje do dodawania, usuwania i wyświetlić listę projektów w pliku rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="8c3b7-164">Options to add, remove, and list projects in a solution file.</span></span>       |
| [<span data-ttu-id="8c3b7-165">dotnet store</span><span class="sxs-lookup"><span data-stu-id="8c3b7-165">dotnet store</span></span>](dotnet-store.md)     | <span data-ttu-id="8c3b7-166">Przechowuje zestawy w magazynie pakietów środowiska wykonawczego.</span><span class="sxs-lookup"><span data-stu-id="8c3b7-166">Stores assemblies in the runtime package store.</span></span>                     |
| [<span data-ttu-id="8c3b7-167">dotnet test</span><span class="sxs-lookup"><span data-stu-id="8c3b7-167">dotnet test</span></span>](dotnet-test.md)       | <span data-ttu-id="8c3b7-168">Uruchamia testy przy użyciu runner testu.</span><span class="sxs-lookup"><span data-stu-id="8c3b7-168">Runs tests using a test runner.</span></span>                                     |

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="8c3b7-169">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="8c3b7-169">.NET Core 1.x</span></span>](#tab/netcore1x)

| <span data-ttu-id="8c3b7-170">Polecenie</span><span class="sxs-lookup"><span data-stu-id="8c3b7-170">Command</span></span>                             | <span data-ttu-id="8c3b7-171">Funkcja</span><span class="sxs-lookup"><span data-stu-id="8c3b7-171">Function</span></span>                                                            |
| ----------------------------------- | ------------------------------------------------------------------- |
| [<span data-ttu-id="8c3b7-172">dotnet build</span><span class="sxs-lookup"><span data-stu-id="8c3b7-172">dotnet build</span></span>](dotnet-build.md)     | <span data-ttu-id="8c3b7-173">Tworzy aplikacji .NET Core.</span><span class="sxs-lookup"><span data-stu-id="8c3b7-173">Builds a .NET Core application.</span></span>                                     |
| [<span data-ttu-id="8c3b7-174">dotnet clean</span><span class="sxs-lookup"><span data-stu-id="8c3b7-174">dotnet clean</span></span>](dotnet-clean.md)     | <span data-ttu-id="8c3b7-175">Wyczyść wyniki do kompilacji.</span><span class="sxs-lookup"><span data-stu-id="8c3b7-175">Clean build outputs.</span></span>                                              |
| [<span data-ttu-id="8c3b7-176">dotnet migrate</span><span class="sxs-lookup"><span data-stu-id="8c3b7-176">dotnet migrate</span></span>](dotnet-migrate.md) | <span data-ttu-id="8c3b7-177">Wykonuje migrację prawidłowy projekt Preview 2 projektu .NET Core SDK 1.0.</span><span class="sxs-lookup"><span data-stu-id="8c3b7-177">Migrates a valid Preview 2 project to a .NET Core SDK 1.0 project.</span></span>  |
| [<span data-ttu-id="8c3b7-178">dotnet msbuild</span><span class="sxs-lookup"><span data-stu-id="8c3b7-178">dotnet msbuild</span></span>](dotnet-msbuild.md) | <span data-ttu-id="8c3b7-179">Zapewnia dostęp do wiersza polecenia programu MSBuild.</span><span class="sxs-lookup"><span data-stu-id="8c3b7-179">Provides access to the MSBuild command line.</span></span>                        |
| [<span data-ttu-id="8c3b7-180">dotnet new</span><span class="sxs-lookup"><span data-stu-id="8c3b7-180">dotnet new</span></span>](dotnet-new.md)         | <span data-ttu-id="8c3b7-181">Inicjuje języka C# lub projektów F # dla danego szablonu.</span><span class="sxs-lookup"><span data-stu-id="8c3b7-181">Initializes a C# or F# project for a given template.</span></span>                |
| [<span data-ttu-id="8c3b7-182">dotnet pack</span><span class="sxs-lookup"><span data-stu-id="8c3b7-182">dotnet pack</span></span>](dotnet-pack.md)       | <span data-ttu-id="8c3b7-183">Tworzy pakiet NuGet kodu.</span><span class="sxs-lookup"><span data-stu-id="8c3b7-183">Creates a NuGet package of your code.</span></span>                               |
| [<span data-ttu-id="8c3b7-184">dotnet publish</span><span class="sxs-lookup"><span data-stu-id="8c3b7-184">dotnet publish</span></span>](dotnet-publish.md) | <span data-ttu-id="8c3b7-185">Publikowanie aplikacji .NET framework zależne lub niezależne.</span><span class="sxs-lookup"><span data-stu-id="8c3b7-185">Publishes a .NET framework-dependent or self-contained application.</span></span> |
| [<span data-ttu-id="8c3b7-186">dotnet restore</span><span class="sxs-lookup"><span data-stu-id="8c3b7-186">dotnet restore</span></span>](dotnet-restore.md) | <span data-ttu-id="8c3b7-187">Przywraca zależności dla danej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="8c3b7-187">Restores the dependencies for a given application.</span></span>                  |
| [<span data-ttu-id="8c3b7-188">dotnet run</span><span class="sxs-lookup"><span data-stu-id="8c3b7-188">dotnet run</span></span>](dotnet-run.md)         | <span data-ttu-id="8c3b7-189">Aplikacja jest uruchamiana ze źródła.</span><span class="sxs-lookup"><span data-stu-id="8c3b7-189">Runs the application from source.</span></span>                                   |
| [<span data-ttu-id="8c3b7-190">dotnet sln</span><span class="sxs-lookup"><span data-stu-id="8c3b7-190">dotnet sln</span></span>](dotnet-sln.md)         | <span data-ttu-id="8c3b7-191">Opcje do dodawania, usuwania i wyświetlić listę projektów w pliku rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="8c3b7-191">Options to add, remove, and list projects in a solution file.</span></span>       |
| [<span data-ttu-id="8c3b7-192">dotnet test</span><span class="sxs-lookup"><span data-stu-id="8c3b7-192">dotnet test</span></span>](dotnet-test.md)       | <span data-ttu-id="8c3b7-193">Uruchamia testy przy użyciu runner testu.</span><span class="sxs-lookup"><span data-stu-id="8c3b7-193">Runs tests using a test runner.</span></span>                                     |

---

### <a name="project-references"></a><span data-ttu-id="8c3b7-194">Odwołania do projektu</span><span class="sxs-lookup"><span data-stu-id="8c3b7-194">Project references</span></span>

<span data-ttu-id="8c3b7-195">Polecenie</span><span class="sxs-lookup"><span data-stu-id="8c3b7-195">Command</span></span> | <span data-ttu-id="8c3b7-196">Funkcja</span><span class="sxs-lookup"><span data-stu-id="8c3b7-196">Function</span></span>
--- | ---
[<span data-ttu-id="8c3b7-197">dotnet add reference</span><span class="sxs-lookup"><span data-stu-id="8c3b7-197">dotnet add reference</span></span>](dotnet-add-reference.md) | <span data-ttu-id="8c3b7-198">Dodaj odwołanie do projektu.</span><span class="sxs-lookup"><span data-stu-id="8c3b7-198">Add a project reference.</span></span>
[<span data-ttu-id="8c3b7-199">dotnet list reference</span><span class="sxs-lookup"><span data-stu-id="8c3b7-199">dotnet list reference</span></span>](dotnet-list-reference.md) | <span data-ttu-id="8c3b7-200">Lista odwołań do projektu.</span><span class="sxs-lookup"><span data-stu-id="8c3b7-200">List project references.</span></span>
[<span data-ttu-id="8c3b7-201">dotnet remove reference</span><span class="sxs-lookup"><span data-stu-id="8c3b7-201">dotnet remove reference</span></span>](dotnet-remove-reference.md) | <span data-ttu-id="8c3b7-202">Usuń odwołanie do projektu.</span><span class="sxs-lookup"><span data-stu-id="8c3b7-202">Remove a project reference.</span></span>

### <a name="nuget-packages"></a><span data-ttu-id="8c3b7-203">Pakiety NuGet</span><span class="sxs-lookup"><span data-stu-id="8c3b7-203">NuGet packages</span></span>

<span data-ttu-id="8c3b7-204">Polecenie</span><span class="sxs-lookup"><span data-stu-id="8c3b7-204">Command</span></span> | <span data-ttu-id="8c3b7-205">Funkcja</span><span class="sxs-lookup"><span data-stu-id="8c3b7-205">Function</span></span>
--- | ---
[<span data-ttu-id="8c3b7-206">dotnet add package</span><span class="sxs-lookup"><span data-stu-id="8c3b7-206">dotnet add package</span></span>](dotnet-add-package.md) | <span data-ttu-id="8c3b7-207">Dodaj pakiet NuGet.</span><span class="sxs-lookup"><span data-stu-id="8c3b7-207">Add a NuGet package.</span></span>
[<span data-ttu-id="8c3b7-208">dotnet remove package</span><span class="sxs-lookup"><span data-stu-id="8c3b7-208">dotnet remove package</span></span>](dotnet-remove-package.md) | <span data-ttu-id="8c3b7-209">Usunięcie pakietu NuGet.</span><span class="sxs-lookup"><span data-stu-id="8c3b7-209">Remove a NuGet package.</span></span>

### <a name="nuget-commands"></a><span data-ttu-id="8c3b7-210">Polecenia NuGet</span><span class="sxs-lookup"><span data-stu-id="8c3b7-210">NuGet commands</span></span>

<span data-ttu-id="8c3b7-211">Polecenie</span><span class="sxs-lookup"><span data-stu-id="8c3b7-211">Command</span></span> | <span data-ttu-id="8c3b7-212">Funkcja</span><span class="sxs-lookup"><span data-stu-id="8c3b7-212">Function</span></span>
--- | ---
[<span data-ttu-id="8c3b7-213">dotnet nuget delete</span><span class="sxs-lookup"><span data-stu-id="8c3b7-213">dotnet nuget delete</span></span>](dotnet-nuget-delete.md) | <span data-ttu-id="8c3b7-214">Usuwa lub unlists pakietu z serwera.</span><span class="sxs-lookup"><span data-stu-id="8c3b7-214">Deletes or unlists a package from the server.</span></span>
[<span data-ttu-id="8c3b7-215">dotnet nuget locals</span><span class="sxs-lookup"><span data-stu-id="8c3b7-215">dotnet nuget locals</span></span>](dotnet-nuget-locals.md) | <span data-ttu-id="8c3b7-216">Czyści lub wyświetla ich listę zasobów lokalnych NuGet np. pamięci podręcznej żądania http, tymczasowego pamięci podręcznej lub folderu packages globalne dla komputera.</span><span class="sxs-lookup"><span data-stu-id="8c3b7-216">Clears or lists local NuGet resources such as http-request cache, temporary cache, or machine-wide global packages folder.</span></span>
[<span data-ttu-id="8c3b7-217">dotnet nuget push</span><span class="sxs-lookup"><span data-stu-id="8c3b7-217">dotnet nuget push</span></span>](dotnet-nuget-push.md) | <span data-ttu-id="8c3b7-218">Wypychanie pakietu do serwera i publikuje ją.</span><span class="sxs-lookup"><span data-stu-id="8c3b7-218">Pushes a package to the server and publishes it.</span></span>

## <a name="examples"></a><span data-ttu-id="8c3b7-219">Przykłady</span><span class="sxs-lookup"><span data-stu-id="8c3b7-219">Examples</span></span>

<span data-ttu-id="8c3b7-220">Inicjowanie przykładowej aplikacji konsoli .NET Core, który można skompilować i uruchomić:</span><span class="sxs-lookup"><span data-stu-id="8c3b7-220">Initialize a sample .NET Core console application that can be compiled and run:</span></span>

`dotnet new console`

<span data-ttu-id="8c3b7-221">Przywróć zależności dla danej aplikacji:</span><span class="sxs-lookup"><span data-stu-id="8c3b7-221">Restore dependencies for a given application:</span></span>

`dotnet restore`

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

<span data-ttu-id="8c3b7-222">Tworzenie projektu i jego zależności w podanym katalogu:</span><span class="sxs-lookup"><span data-stu-id="8c3b7-222">Build a project and its dependencies in a given directory:</span></span>

`dotnet build`

<span data-ttu-id="8c3b7-223">Uruchamianie aplikacji zależnych od framework o nazwie `myapp.dll`:</span><span class="sxs-lookup"><span data-stu-id="8c3b7-223">Run a framework-dependent app named `myapp.dll`:</span></span>

`dotnet myapp.dll`

## <a name="environment-variables"></a><span data-ttu-id="8c3b7-224">Zmienne środowiskowe</span><span class="sxs-lookup"><span data-stu-id="8c3b7-224">Environment variables</span></span>

`DOTNET_PACKAGES`

<span data-ttu-id="8c3b7-225">Pakiet główny pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="8c3b7-225">The primary package cache.</span></span> <span data-ttu-id="8c3b7-226">Jeśli nie został ustawiony, domyślnie `$HOME/.nuget/packages` w systemie Unix lub `%HOME%\NuGet\Packages` w systemie Windows.</span><span class="sxs-lookup"><span data-stu-id="8c3b7-226">If not set, it defaults to `$HOME/.nuget/packages` on Unix or `%HOME%\NuGet\Packages` on Windows.</span></span>

`DOTNET_SERVICING`

<span data-ttu-id="8c3b7-227">Określa lokalizację obsługi indeksu jest używany przez hosta udostępnionych podczas ładowania środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="8c3b7-227">Specifies the location of the servicing index to use by the shared host when loading the runtime.</span></span>

`DOTNET_CLI_TELEMETRY_OPTOUT`

<span data-ttu-id="8c3b7-228">Określa, czy dane dotyczące użycia narzędzia .NET Core został zebrany i wysyłany do firmy Microsoft.</span><span class="sxs-lookup"><span data-stu-id="8c3b7-228">Specifies whether data about the .NET Core tools usage is collected and sent to Microsoft.</span></span> <span data-ttu-id="8c3b7-229">Ustaw `true` Aby zrezygnować z funkcji telemetrii (wartości `true`, `1`, lub `yes` zaakceptowane), w przeciwnym razie należy ustawić `false` w funkcji telemetrii (wartości `false`, `0`, lub `no` akceptowane).</span><span class="sxs-lookup"><span data-stu-id="8c3b7-229">Set to `true` to opt-out of the telemetry feature (values `true`, `1`, or `yes` accepted); otherwise, set to `false` to opt-in to the telemetry features (values `false`, `0`, or `no` accepted).</span></span> <span data-ttu-id="8c3b7-230">Jeśli nie jest ustawiony, wartości domyślne jest `false`, i funkcja telemetrii jest aktywna.</span><span class="sxs-lookup"><span data-stu-id="8c3b7-230">If not set, the defaults is `false`, and the telemetry feature is active.</span></span>
