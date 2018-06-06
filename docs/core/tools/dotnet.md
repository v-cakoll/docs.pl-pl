---
title: polecenie DotNet - .NET Core interfejsu wiersza polecenia
description: Informacje o poleceniu dotnet (ogólnego sterownik narzędzi interfejsu wiersza polecenia platformy .NET Core) i jej użycia.
author: mairaw
ms.author: mairaw
ms.date: 06/04/2018
ms.openlocfilehash: 788dc746705f9328683019ab3ad9836204a1ea63
ms.sourcegitcommit: fc70fcb9c789b6a4aefcdace46f3643fd076450f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2018
ms.locfileid: "34805662"
---
# <a name="dotnet-command"></a><span data-ttu-id="4864a-103">polecenie DotNet</span><span class="sxs-lookup"><span data-stu-id="4864a-103">dotnet command</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="4864a-104">Nazwa</span><span class="sxs-lookup"><span data-stu-id="4864a-104">Name</span></span>

<span data-ttu-id="4864a-105">`dotnet` -Ogólne sterownik do uruchamiania polecenia wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="4864a-105">`dotnet` - General driver for running the command-line commands.</span></span>

## <a name="synopsis"></a><span data-ttu-id="4864a-106">Streszczenie</span><span class="sxs-lookup"><span data-stu-id="4864a-106">Synopsis</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="4864a-107">Oprogramowanie .NET core 2.1</span><span class="sxs-lookup"><span data-stu-id="4864a-107">.NET Core 2.1</span></span>](#tab/netcore21)
```
dotnet [command] [arguments] [--additional-deps] [--additionalprobingpath] [-d|--diagnostics] [--fx-version]
    [-h|--help] [--info] [--list-runtimes] [--list-sdks] [--roll-forward-on-no-candidate-fx] [-v|--verbosity] [--version]
```
# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="4864a-108">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="4864a-108">.NET Core 2.0</span></span>](#tab/netcore20)
```
dotnet [command] [arguments] [--additional-deps] [--additionalprobingpath] [-d|--diagnostics]
    [--fx-version] [-h|--help] [--info] [--roll-forward-on-no-candidate-fx] [-v|--verbosity] [--version]
```
# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="4864a-109">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="4864a-109">.NET Core 1.x</span></span>](#tab/netcore1x)
```
dotnet [command] [arguments] [--additionalprobingpath] [-d|--diagnostics] [--fx-version]
    [-h|--help] [--info] [-v|--verbosity] [--version]
```
---

## <a name="description"></a><span data-ttu-id="4864a-110">Opis</span><span class="sxs-lookup"><span data-stu-id="4864a-110">Description</span></span>

<span data-ttu-id="4864a-111">`dotnet` jest ogólny sterownik łańcuch narzędzi interfejsu wiersza polecenia (CLI).</span><span class="sxs-lookup"><span data-stu-id="4864a-111">`dotnet` is a generic driver for the Command Line Interface (CLI) toolchain.</span></span> <span data-ttu-id="4864a-112">Wywoływane na jego własnej, zapewnia użycia krótkie instrukcje.</span><span class="sxs-lookup"><span data-stu-id="4864a-112">Invoked on its own, it provides brief usage instructions.</span></span>

<span data-ttu-id="4864a-113">Każdej z funkcji jest implementowany jako polecenia.</span><span class="sxs-lookup"><span data-stu-id="4864a-113">Each specific feature is implemented as a command.</span></span> <span data-ttu-id="4864a-114">Do korzystania z funkcji określono polecenia po `dotnet`, takich jak [ `dotnet build` ](dotnet-build.md).</span><span class="sxs-lookup"><span data-stu-id="4864a-114">To use the feature, the command is specified after `dotnet`, such as [`dotnet build`](dotnet-build.md).</span></span> <span data-ttu-id="4864a-115">Wszystkie argumenty następujące polecenie to własną argumentów.</span><span class="sxs-lookup"><span data-stu-id="4864a-115">All of the arguments following the command are its own arguments.</span></span>

<span data-ttu-id="4864a-116">Tylko `dotnet` jest używany jako polecenia samodzielnie [aplikacje zależne od framework](../deploying/index.md).</span><span class="sxs-lookup"><span data-stu-id="4864a-116">The only time `dotnet` is used as a command on its own is to run [framework-dependent apps](../deploying/index.md).</span></span> <span data-ttu-id="4864a-117">Określ aplikację DLL po `dotnet` zlecenie do wykonywania aplikacji (na przykład `dotnet myapp.dll`).</span><span class="sxs-lookup"><span data-stu-id="4864a-117">Specify an application DLL after the `dotnet` verb to execute the application (for example, `dotnet myapp.dll`).</span></span>

## <a name="options"></a><span data-ttu-id="4864a-118">Opcje</span><span class="sxs-lookup"><span data-stu-id="4864a-118">Options</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="4864a-119">Oprogramowanie .NET core 2.1</span><span class="sxs-lookup"><span data-stu-id="4864a-119">.NET Core 2.1</span></span>](#tab/netcore21)

`--additional-deps <PATH>`

<span data-ttu-id="4864a-120">Ścieżka do dodatkowych *deps.json* pliku.</span><span class="sxs-lookup"><span data-stu-id="4864a-120">Path to additional *deps.json* file.</span></span>

`--additionalprobingpath <PATH>`

<span data-ttu-id="4864a-121">Ścieżka zawierające sondowania zasad i zestawów do sondowania.</span><span class="sxs-lookup"><span data-stu-id="4864a-121">Path containing probing policy and assemblies to probe.</span></span>

`-d|--diagnostics`

<span data-ttu-id="4864a-122">Umożliwia wyjście diagnostyczne.</span><span class="sxs-lookup"><span data-stu-id="4864a-122">Enables diagnostic output.</span></span>

`--fx-version <VERSION>`

<span data-ttu-id="4864a-123">Wersja zainstalowanego środowiska uruchomieniowego .NET Core służące do uruchamiania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="4864a-123">Version of the installed .NET Core runtime to use to run the application.</span></span>

`-h|--help`

<span data-ttu-id="4864a-124">Drukuje krótkich pomocy dla polecenia.</span><span class="sxs-lookup"><span data-stu-id="4864a-124">Prints out a short help for the command.</span></span> <span data-ttu-id="4864a-125">Jeśli używany z `dotnet`, również Wyświetla listę dostępnych poleceń.</span><span class="sxs-lookup"><span data-stu-id="4864a-125">If using with `dotnet`, it also prints a list of the available commands.</span></span>

`--info`

<span data-ttu-id="4864a-126">Drukuje szczegółowe informacje na temat narzędzi interfejsu wiersza polecenia i środowiska, takich jak bieżący system operacyjny, Zatwierdź SHA dla wersji i innych informacji.</span><span class="sxs-lookup"><span data-stu-id="4864a-126">Prints out detailed information about the CLI tooling and the environment, such as the current operating system, commit SHA for the version, and other information.</span></span>

`--list-runtimes`

<span data-ttu-id="4864a-127">Wyświetla zainstalowane środowiska wykonawczego platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="4864a-127">Displays the installed .NET Core runtimes.</span></span>

`--list-sdks`

<span data-ttu-id="4864a-128">Wyświetla zainstalowane zestawy SDK Core .NET.</span><span class="sxs-lookup"><span data-stu-id="4864a-128">Displays the installed .NET Core SDKs.</span></span>

`--roll-forward-on-no-candidate-fx`

 <span data-ttu-id="4864a-129">Przedstawia przekazywania na ma kandydata framework udostępnionego.</span><span class="sxs-lookup"><span data-stu-id="4864a-129">Rolls forward on no candidate shared framework.</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="4864a-130">Ustawia poziom szczegółowości polecenia.</span><span class="sxs-lookup"><span data-stu-id="4864a-130">Sets the verbosity level of the command.</span></span> <span data-ttu-id="4864a-131">Dozwolone wartości to `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, i `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="4864a-131">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="4864a-132">Nie są obsługiwane w każdym poleceniu; zobacz stronę danego polecenia, aby ustalić, czy ta opcja jest dostępna.</span><span class="sxs-lookup"><span data-stu-id="4864a-132">Not supported in every command; see specific command page to determine if this option is available.</span></span>

`--version`

<span data-ttu-id="4864a-133">Drukuje wersji programu .NET Core SDK w użyciu.</span><span class="sxs-lookup"><span data-stu-id="4864a-133">Prints out the version of the .NET Core SDK in use.</span></span>

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="4864a-134">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="4864a-134">.NET Core 2.0</span></span>](#tab/netcore20)

`--additional-deps <PATH>`

<span data-ttu-id="4864a-135">Ścieżka do dodatkowych *deps.json* pliku.</span><span class="sxs-lookup"><span data-stu-id="4864a-135">Path to additional *deps.json* file.</span></span>

`--additionalprobingpath <PATH>`

<span data-ttu-id="4864a-136">Ścieżka zawierające sondowania zasad i zestawów do sondowania.</span><span class="sxs-lookup"><span data-stu-id="4864a-136">Path containing probing policy and assemblies to probe.</span></span>

`-d|--diagnostics`

<span data-ttu-id="4864a-137">Umożliwia wyjście diagnostyczne.</span><span class="sxs-lookup"><span data-stu-id="4864a-137">Enables diagnostic output.</span></span>

`--fx-version <VERSION>`

<span data-ttu-id="4864a-138">Wersja zainstalowanego środowiska uruchomieniowego .NET Core służące do uruchamiania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="4864a-138">Version of the installed .NET Core runtime to use to run the application.</span></span>

`-h|--help`

<span data-ttu-id="4864a-139">Drukuje krótkich pomocy dla polecenia.</span><span class="sxs-lookup"><span data-stu-id="4864a-139">Prints out a short help for the command.</span></span> <span data-ttu-id="4864a-140">Jeśli używany z `dotnet`, również Wyświetla listę dostępnych poleceń.</span><span class="sxs-lookup"><span data-stu-id="4864a-140">If using with `dotnet`, it also prints a list of the available commands.</span></span>

`--info`

<span data-ttu-id="4864a-141">Drukuje szczegółowe informacje na temat narzędzi interfejsu wiersza polecenia i środowiska, takich jak bieżący system operacyjny, Zatwierdź SHA dla wersji i innych informacji.</span><span class="sxs-lookup"><span data-stu-id="4864a-141">Prints out detailed information about the CLI tooling and the environment, such as the current operating system, commit SHA for the version, and other information.</span></span>

`--roll-forward-on-no-candidate-fx`

 <span data-ttu-id="4864a-142">Przedstawia przekazywania na ma kandydata framework udostępnionego.</span><span class="sxs-lookup"><span data-stu-id="4864a-142">Rolls forward on no candidate shared framework.</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="4864a-143">Ustawia poziom szczegółowości polecenia.</span><span class="sxs-lookup"><span data-stu-id="4864a-143">Sets the verbosity level of the command.</span></span> <span data-ttu-id="4864a-144">Dozwolone wartości to `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, i `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="4864a-144">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="4864a-145">Nie są obsługiwane w każdym poleceniu; zobacz stronę danego polecenia, aby ustalić, czy ta opcja jest dostępna.</span><span class="sxs-lookup"><span data-stu-id="4864a-145">Not supported in every command; see specific command page to determine if this option is available.</span></span>

`--version`

<span data-ttu-id="4864a-146">Drukuje wersji programu .NET Core SDK w użyciu.</span><span class="sxs-lookup"><span data-stu-id="4864a-146">Prints out the version of the .NET Core SDK in use.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="4864a-147">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="4864a-147">.NET Core 1.x</span></span>](#tab/netcore1x)

`--additionalprobingpath <PATH>`

<span data-ttu-id="4864a-148">Ścieżka zawierające sondowania zasad i zestawów do sondowania.</span><span class="sxs-lookup"><span data-stu-id="4864a-148">Path containing probing policy and assemblies to probe.</span></span>

`-d|--diagnostics`

<span data-ttu-id="4864a-149">Umożliwia wyjście diagnostyczne.</span><span class="sxs-lookup"><span data-stu-id="4864a-149">Enables diagnostic output.</span></span>

`--fx-version <VERSION>`

<span data-ttu-id="4864a-150">Wersja zainstalowanego środowiska uruchomieniowego .NET Core służące do uruchamiania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="4864a-150">Version of the installed .NET Core runtime to use to run the application.</span></span>

`-h|--help`

<span data-ttu-id="4864a-151">Drukuje krótkich pomocy dla polecenia.</span><span class="sxs-lookup"><span data-stu-id="4864a-151">Prints out a short help for the command.</span></span> <span data-ttu-id="4864a-152">Jeśli używany z `dotnet`, również Wyświetla listę dostępnych poleceń.</span><span class="sxs-lookup"><span data-stu-id="4864a-152">If using with `dotnet`, it also prints a list of the available commands.</span></span>

`--info`

<span data-ttu-id="4864a-153">Drukuje szczegółowe informacje na temat narzędzi interfejsu wiersza polecenia i środowiska, takich jak bieżący system operacyjny, Zatwierdź SHA dla wersji i innych informacji.</span><span class="sxs-lookup"><span data-stu-id="4864a-153">Prints out detailed information about the CLI tooling and the environment, such as the current operating system, commit SHA for the version, and other information.</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="4864a-154">Ustawia poziom szczegółowości polecenia.</span><span class="sxs-lookup"><span data-stu-id="4864a-154">Sets the verbosity level of the command.</span></span> <span data-ttu-id="4864a-155">Dozwolone wartości to `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, i `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="4864a-155">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="4864a-156">Nie są obsługiwane w każdym poleceniu; zobacz stronę danego polecenia, aby ustalić, czy ta opcja jest dostępna.</span><span class="sxs-lookup"><span data-stu-id="4864a-156">Not supported in every command; see specific command page to determine if this option is available.</span></span>

`--version`

<span data-ttu-id="4864a-157">Drukuje wersji programu .NET Core SDK w użyciu.</span><span class="sxs-lookup"><span data-stu-id="4864a-157">Prints out the version of the .NET Core SDK in use.</span></span>

---

## <a name="dotnet-commands"></a><span data-ttu-id="4864a-158">polecenia DotNet</span><span class="sxs-lookup"><span data-stu-id="4864a-158">dotnet commands</span></span>

### <a name="general"></a><span data-ttu-id="4864a-159">Ogólne</span><span class="sxs-lookup"><span data-stu-id="4864a-159">General</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="4864a-160">Oprogramowanie .NET core 2.1</span><span class="sxs-lookup"><span data-stu-id="4864a-160">.NET Core 2.1</span></span>](#tab/netcore21)

| <span data-ttu-id="4864a-161">Polecenie</span><span class="sxs-lookup"><span data-stu-id="4864a-161">Command</span></span>                                       | <span data-ttu-id="4864a-162">Funkcja</span><span class="sxs-lookup"><span data-stu-id="4864a-162">Function</span></span>                                                            |
| --------------------------------------------- | ------------------------------------------------------------------- |
| [<span data-ttu-id="4864a-163">dotnet build</span><span class="sxs-lookup"><span data-stu-id="4864a-163">dotnet build</span></span>](dotnet-build.md)               | <span data-ttu-id="4864a-164">Tworzy aplikacji .NET Core.</span><span class="sxs-lookup"><span data-stu-id="4864a-164">Builds a .NET Core application.</span></span>                                     |
| [<span data-ttu-id="4864a-165">Serwer kompilacji DotNet</span><span class="sxs-lookup"><span data-stu-id="4864a-165">dotnet build-server</span></span>](dotnet-build-server.md) | <span data-ttu-id="4864a-166">Wchodzi w interakcję z serwerami uruchomione przez kompilację.</span><span class="sxs-lookup"><span data-stu-id="4864a-166">Interacts with servers started by a build.</span></span>                          |
| [<span data-ttu-id="4864a-167">dotnet clean</span><span class="sxs-lookup"><span data-stu-id="4864a-167">dotnet clean</span></span>](dotnet-clean.md)               | <span data-ttu-id="4864a-168">Wyczyść wyniki do kompilacji.</span><span class="sxs-lookup"><span data-stu-id="4864a-168">Clean build outputs.</span></span>                                                |
| [<span data-ttu-id="4864a-169">dotnet help</span><span class="sxs-lookup"><span data-stu-id="4864a-169">dotnet help</span></span>](dotnet-help.md)                 | <span data-ttu-id="4864a-170">Przedstawia szczegółowe dokumentacji online dla polecenia.</span><span class="sxs-lookup"><span data-stu-id="4864a-170">Shows more detailed documentation online for the command.</span></span>           |
| [<span data-ttu-id="4864a-171">dotnet migrate</span><span class="sxs-lookup"><span data-stu-id="4864a-171">dotnet migrate</span></span>](dotnet-migrate.md)           | <span data-ttu-id="4864a-172">Wykonuje migrację prawidłowy projekt Preview 2 projektu .NET Core SDK 1.0.</span><span class="sxs-lookup"><span data-stu-id="4864a-172">Migrates a valid Preview 2 project to a .NET Core SDK 1.0 project.</span></span>  |
| [<span data-ttu-id="4864a-173">dotnet msbuild</span><span class="sxs-lookup"><span data-stu-id="4864a-173">dotnet msbuild</span></span>](dotnet-msbuild.md)           | <span data-ttu-id="4864a-174">Zapewnia dostęp do wiersza polecenia programu MSBuild.</span><span class="sxs-lookup"><span data-stu-id="4864a-174">Provides access to the MSBuild command line.</span></span>                        |
| [<span data-ttu-id="4864a-175">dotnet new</span><span class="sxs-lookup"><span data-stu-id="4864a-175">dotnet new</span></span>](dotnet-new.md)                   | <span data-ttu-id="4864a-176">Inicjuje języka C# lub projektów F # dla danego szablonu.</span><span class="sxs-lookup"><span data-stu-id="4864a-176">Initializes a C# or F# project for a given template.</span></span>                |
| [<span data-ttu-id="4864a-177">dotnet pack</span><span class="sxs-lookup"><span data-stu-id="4864a-177">dotnet pack</span></span>](dotnet-pack.md)                 | <span data-ttu-id="4864a-178">Tworzy pakiet NuGet kodu.</span><span class="sxs-lookup"><span data-stu-id="4864a-178">Creates a NuGet package of your code.</span></span>                               |
| [<span data-ttu-id="4864a-179">dotnet publish</span><span class="sxs-lookup"><span data-stu-id="4864a-179">dotnet publish</span></span>](dotnet-publish.md)           | <span data-ttu-id="4864a-180">Publikowanie aplikacji .NET framework zależne lub niezależne.</span><span class="sxs-lookup"><span data-stu-id="4864a-180">Publishes a .NET framework-dependent or self-contained application.</span></span> |
| [<span data-ttu-id="4864a-181">dotnet restore</span><span class="sxs-lookup"><span data-stu-id="4864a-181">dotnet restore</span></span>](dotnet-restore.md)           | <span data-ttu-id="4864a-182">Przywraca zależności dla danej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="4864a-182">Restores the dependencies for a given application.</span></span>                  |
| [<span data-ttu-id="4864a-183">dotnet run</span><span class="sxs-lookup"><span data-stu-id="4864a-183">dotnet run</span></span>](dotnet-run.md)                   | <span data-ttu-id="4864a-184">Aplikacja jest uruchamiana ze źródła.</span><span class="sxs-lookup"><span data-stu-id="4864a-184">Runs the application from source.</span></span>                                   |
| [<span data-ttu-id="4864a-185">dotnet sln</span><span class="sxs-lookup"><span data-stu-id="4864a-185">dotnet sln</span></span>](dotnet-sln.md)                   | <span data-ttu-id="4864a-186">Opcje do dodawania, usuwania i wyświetlić listę projektów w pliku rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="4864a-186">Options to add, remove, and list projects in a solution file.</span></span>       |
| [<span data-ttu-id="4864a-187">dotnet store</span><span class="sxs-lookup"><span data-stu-id="4864a-187">dotnet store</span></span>](dotnet-store.md)               | <span data-ttu-id="4864a-188">Przechowuje zestawy w magazynie pakietów środowiska wykonawczego.</span><span class="sxs-lookup"><span data-stu-id="4864a-188">Stores assemblies in the runtime package store.</span></span>                     |
| [<span data-ttu-id="4864a-189">dotnet test</span><span class="sxs-lookup"><span data-stu-id="4864a-189">dotnet test</span></span>](dotnet-test.md)                 | <span data-ttu-id="4864a-190">Uruchamia testy przy użyciu runner testu.</span><span class="sxs-lookup"><span data-stu-id="4864a-190">Runs tests using a test runner.</span></span>                                     |

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="4864a-191">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="4864a-191">.NET Core 2.0</span></span>](#tab/netcore20)

| <span data-ttu-id="4864a-192">Polecenie</span><span class="sxs-lookup"><span data-stu-id="4864a-192">Command</span></span>                             | <span data-ttu-id="4864a-193">Funkcja</span><span class="sxs-lookup"><span data-stu-id="4864a-193">Function</span></span>                                                            |
| ----------------------------------- | ------------------------------------------------------------------- |
| [<span data-ttu-id="4864a-194">dotnet build</span><span class="sxs-lookup"><span data-stu-id="4864a-194">dotnet build</span></span>](dotnet-build.md)     | <span data-ttu-id="4864a-195">Tworzy aplikacji .NET Core.</span><span class="sxs-lookup"><span data-stu-id="4864a-195">Builds a .NET Core application.</span></span>                                     |
| [<span data-ttu-id="4864a-196">dotnet clean</span><span class="sxs-lookup"><span data-stu-id="4864a-196">dotnet clean</span></span>](dotnet-clean.md)     | <span data-ttu-id="4864a-197">Wyczyść wyniki do kompilacji.</span><span class="sxs-lookup"><span data-stu-id="4864a-197">Clean build outputs.</span></span>                                              |
| [<span data-ttu-id="4864a-198">dotnet help</span><span class="sxs-lookup"><span data-stu-id="4864a-198">dotnet help</span></span>](dotnet-help.md)       | <span data-ttu-id="4864a-199">Przedstawia szczegółowe dokumentacji online dla polecenia.</span><span class="sxs-lookup"><span data-stu-id="4864a-199">Shows more detailed documentation online for the command.</span></span>           |
| [<span data-ttu-id="4864a-200">dotnet migrate</span><span class="sxs-lookup"><span data-stu-id="4864a-200">dotnet migrate</span></span>](dotnet-migrate.md) | <span data-ttu-id="4864a-201">Wykonuje migrację prawidłowy projekt Preview 2 projektu .NET Core SDK 1.0.</span><span class="sxs-lookup"><span data-stu-id="4864a-201">Migrates a valid Preview 2 project to a .NET Core SDK 1.0 project.</span></span>  |
| [<span data-ttu-id="4864a-202">dotnet msbuild</span><span class="sxs-lookup"><span data-stu-id="4864a-202">dotnet msbuild</span></span>](dotnet-msbuild.md) | <span data-ttu-id="4864a-203">Zapewnia dostęp do wiersza polecenia programu MSBuild.</span><span class="sxs-lookup"><span data-stu-id="4864a-203">Provides access to the MSBuild command line.</span></span>                        |
| [<span data-ttu-id="4864a-204">dotnet new</span><span class="sxs-lookup"><span data-stu-id="4864a-204">dotnet new</span></span>](dotnet-new.md)         | <span data-ttu-id="4864a-205">Inicjuje języka C# lub projektów F # dla danego szablonu.</span><span class="sxs-lookup"><span data-stu-id="4864a-205">Initializes a C# or F# project for a given template.</span></span>                |
| [<span data-ttu-id="4864a-206">dotnet pack</span><span class="sxs-lookup"><span data-stu-id="4864a-206">dotnet pack</span></span>](dotnet-pack.md)       | <span data-ttu-id="4864a-207">Tworzy pakiet NuGet kodu.</span><span class="sxs-lookup"><span data-stu-id="4864a-207">Creates a NuGet package of your code.</span></span>                               |
| [<span data-ttu-id="4864a-208">dotnet publish</span><span class="sxs-lookup"><span data-stu-id="4864a-208">dotnet publish</span></span>](dotnet-publish.md) | <span data-ttu-id="4864a-209">Publikowanie aplikacji .NET framework zależne lub niezależne.</span><span class="sxs-lookup"><span data-stu-id="4864a-209">Publishes a .NET framework-dependent or self-contained application.</span></span> |
| [<span data-ttu-id="4864a-210">dotnet restore</span><span class="sxs-lookup"><span data-stu-id="4864a-210">dotnet restore</span></span>](dotnet-restore.md) | <span data-ttu-id="4864a-211">Przywraca zależności dla danej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="4864a-211">Restores the dependencies for a given application.</span></span>                  |
| [<span data-ttu-id="4864a-212">dotnet run</span><span class="sxs-lookup"><span data-stu-id="4864a-212">dotnet run</span></span>](dotnet-run.md)         | <span data-ttu-id="4864a-213">Aplikacja jest uruchamiana ze źródła.</span><span class="sxs-lookup"><span data-stu-id="4864a-213">Runs the application from source.</span></span>                                   |
| [<span data-ttu-id="4864a-214">dotnet sln</span><span class="sxs-lookup"><span data-stu-id="4864a-214">dotnet sln</span></span>](dotnet-sln.md)         | <span data-ttu-id="4864a-215">Opcje do dodawania, usuwania i wyświetlić listę projektów w pliku rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="4864a-215">Options to add, remove, and list projects in a solution file.</span></span>       |
| [<span data-ttu-id="4864a-216">dotnet store</span><span class="sxs-lookup"><span data-stu-id="4864a-216">dotnet store</span></span>](dotnet-store.md)     | <span data-ttu-id="4864a-217">Przechowuje zestawy w magazynie pakietów środowiska wykonawczego.</span><span class="sxs-lookup"><span data-stu-id="4864a-217">Stores assemblies in the runtime package store.</span></span>                     |
| [<span data-ttu-id="4864a-218">dotnet test</span><span class="sxs-lookup"><span data-stu-id="4864a-218">dotnet test</span></span>](dotnet-test.md)       | <span data-ttu-id="4864a-219">Uruchamia testy przy użyciu runner testu.</span><span class="sxs-lookup"><span data-stu-id="4864a-219">Runs tests using a test runner.</span></span>                                     |

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="4864a-220">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="4864a-220">.NET Core 1.x</span></span>](#tab/netcore1x)

| <span data-ttu-id="4864a-221">Polecenie</span><span class="sxs-lookup"><span data-stu-id="4864a-221">Command</span></span>                             | <span data-ttu-id="4864a-222">Funkcja</span><span class="sxs-lookup"><span data-stu-id="4864a-222">Function</span></span>                                                            |
| ----------------------------------- | ------------------------------------------------------------------- |
| [<span data-ttu-id="4864a-223">dotnet build</span><span class="sxs-lookup"><span data-stu-id="4864a-223">dotnet build</span></span>](dotnet-build.md)     | <span data-ttu-id="4864a-224">Tworzy aplikacji .NET Core.</span><span class="sxs-lookup"><span data-stu-id="4864a-224">Builds a .NET Core application.</span></span>                                     |
| [<span data-ttu-id="4864a-225">dotnet clean</span><span class="sxs-lookup"><span data-stu-id="4864a-225">dotnet clean</span></span>](dotnet-clean.md)     | <span data-ttu-id="4864a-226">Wyczyść wyniki do kompilacji.</span><span class="sxs-lookup"><span data-stu-id="4864a-226">Clean build outputs.</span></span>                                              |
| [<span data-ttu-id="4864a-227">dotnet migrate</span><span class="sxs-lookup"><span data-stu-id="4864a-227">dotnet migrate</span></span>](dotnet-migrate.md) | <span data-ttu-id="4864a-228">Wykonuje migrację prawidłowy projekt Preview 2 projektu .NET Core SDK 1.0.</span><span class="sxs-lookup"><span data-stu-id="4864a-228">Migrates a valid Preview 2 project to a .NET Core SDK 1.0 project.</span></span>  |
| [<span data-ttu-id="4864a-229">dotnet msbuild</span><span class="sxs-lookup"><span data-stu-id="4864a-229">dotnet msbuild</span></span>](dotnet-msbuild.md) | <span data-ttu-id="4864a-230">Zapewnia dostęp do wiersza polecenia programu MSBuild.</span><span class="sxs-lookup"><span data-stu-id="4864a-230">Provides access to the MSBuild command line.</span></span>                        |
| [<span data-ttu-id="4864a-231">dotnet new</span><span class="sxs-lookup"><span data-stu-id="4864a-231">dotnet new</span></span>](dotnet-new.md)         | <span data-ttu-id="4864a-232">Inicjuje języka C# lub projektów F # dla danego szablonu.</span><span class="sxs-lookup"><span data-stu-id="4864a-232">Initializes a C# or F# project for a given template.</span></span>                |
| [<span data-ttu-id="4864a-233">dotnet pack</span><span class="sxs-lookup"><span data-stu-id="4864a-233">dotnet pack</span></span>](dotnet-pack.md)       | <span data-ttu-id="4864a-234">Tworzy pakiet NuGet kodu.</span><span class="sxs-lookup"><span data-stu-id="4864a-234">Creates a NuGet package of your code.</span></span>                               |
| [<span data-ttu-id="4864a-235">dotnet publish</span><span class="sxs-lookup"><span data-stu-id="4864a-235">dotnet publish</span></span>](dotnet-publish.md) | <span data-ttu-id="4864a-236">Publikowanie aplikacji .NET framework zależne lub niezależne.</span><span class="sxs-lookup"><span data-stu-id="4864a-236">Publishes a .NET framework-dependent or self-contained application.</span></span> |
| [<span data-ttu-id="4864a-237">dotnet restore</span><span class="sxs-lookup"><span data-stu-id="4864a-237">dotnet restore</span></span>](dotnet-restore.md) | <span data-ttu-id="4864a-238">Przywraca zależności dla danej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="4864a-238">Restores the dependencies for a given application.</span></span>                  |
| [<span data-ttu-id="4864a-239">dotnet run</span><span class="sxs-lookup"><span data-stu-id="4864a-239">dotnet run</span></span>](dotnet-run.md)         | <span data-ttu-id="4864a-240">Aplikacja jest uruchamiana ze źródła.</span><span class="sxs-lookup"><span data-stu-id="4864a-240">Runs the application from source.</span></span>                                   |
| [<span data-ttu-id="4864a-241">dotnet sln</span><span class="sxs-lookup"><span data-stu-id="4864a-241">dotnet sln</span></span>](dotnet-sln.md)         | <span data-ttu-id="4864a-242">Opcje do dodawania, usuwania i wyświetlić listę projektów w pliku rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="4864a-242">Options to add, remove, and list projects in a solution file.</span></span>       |
| [<span data-ttu-id="4864a-243">dotnet test</span><span class="sxs-lookup"><span data-stu-id="4864a-243">dotnet test</span></span>](dotnet-test.md)       | <span data-ttu-id="4864a-244">Uruchamia testy przy użyciu runner testu.</span><span class="sxs-lookup"><span data-stu-id="4864a-244">Runs tests using a test runner.</span></span>                                     |

---

### <a name="project-references"></a><span data-ttu-id="4864a-245">Odwołania do projektu</span><span class="sxs-lookup"><span data-stu-id="4864a-245">Project references</span></span>

<span data-ttu-id="4864a-246">Polecenie</span><span class="sxs-lookup"><span data-stu-id="4864a-246">Command</span></span> | <span data-ttu-id="4864a-247">Funkcja</span><span class="sxs-lookup"><span data-stu-id="4864a-247">Function</span></span>
--- | ---
[<span data-ttu-id="4864a-248">dotnet add reference</span><span class="sxs-lookup"><span data-stu-id="4864a-248">dotnet add reference</span></span>](dotnet-add-reference.md) | <span data-ttu-id="4864a-249">Dodaje odwołanie do projektu.</span><span class="sxs-lookup"><span data-stu-id="4864a-249">Adds a project reference.</span></span>
[<span data-ttu-id="4864a-250">dotnet list reference</span><span class="sxs-lookup"><span data-stu-id="4864a-250">dotnet list reference</span></span>](dotnet-list-reference.md) | <span data-ttu-id="4864a-251">Wyświetla listę odwołań do projektu.</span><span class="sxs-lookup"><span data-stu-id="4864a-251">Lists project references.</span></span>
[<span data-ttu-id="4864a-252">dotnet remove reference</span><span class="sxs-lookup"><span data-stu-id="4864a-252">dotnet remove reference</span></span>](dotnet-remove-reference.md) | <span data-ttu-id="4864a-253">Usuwa odwołanie do projektu.</span><span class="sxs-lookup"><span data-stu-id="4864a-253">Removes a project reference.</span></span>

### <a name="nuget-packages"></a><span data-ttu-id="4864a-254">Pakiety NuGet</span><span class="sxs-lookup"><span data-stu-id="4864a-254">NuGet packages</span></span>

<span data-ttu-id="4864a-255">Polecenie</span><span class="sxs-lookup"><span data-stu-id="4864a-255">Command</span></span> | <span data-ttu-id="4864a-256">Funkcja</span><span class="sxs-lookup"><span data-stu-id="4864a-256">Function</span></span>
--- | ---
[<span data-ttu-id="4864a-257">dotnet add package</span><span class="sxs-lookup"><span data-stu-id="4864a-257">dotnet add package</span></span>](dotnet-add-package.md) | <span data-ttu-id="4864a-258">Dodaje pakiet NuGet.</span><span class="sxs-lookup"><span data-stu-id="4864a-258">Adds a NuGet package.</span></span>
[<span data-ttu-id="4864a-259">dotnet remove package</span><span class="sxs-lookup"><span data-stu-id="4864a-259">dotnet remove package</span></span>](dotnet-remove-package.md) | <span data-ttu-id="4864a-260">Usuwa pakiet NuGet.</span><span class="sxs-lookup"><span data-stu-id="4864a-260">Removes a NuGet package.</span></span>

### <a name="nuget-commands"></a><span data-ttu-id="4864a-261">Polecenia NuGet</span><span class="sxs-lookup"><span data-stu-id="4864a-261">NuGet commands</span></span>

<span data-ttu-id="4864a-262">Polecenie</span><span class="sxs-lookup"><span data-stu-id="4864a-262">Command</span></span> | <span data-ttu-id="4864a-263">Funkcja</span><span class="sxs-lookup"><span data-stu-id="4864a-263">Function</span></span>
--- | ---
[<span data-ttu-id="4864a-264">dotnet nuget delete</span><span class="sxs-lookup"><span data-stu-id="4864a-264">dotnet nuget delete</span></span>](dotnet-nuget-delete.md) | <span data-ttu-id="4864a-265">Usuwa lub unlists pakietu z serwera.</span><span class="sxs-lookup"><span data-stu-id="4864a-265">Deletes or unlists a package from the server.</span></span>
[<span data-ttu-id="4864a-266">dotnet nuget locals</span><span class="sxs-lookup"><span data-stu-id="4864a-266">dotnet nuget locals</span></span>](dotnet-nuget-locals.md) | <span data-ttu-id="4864a-267">Czyści lub wyświetla ich listę zasobów lokalnych NuGet np. pamięci podręcznej żądania http, tymczasowego pamięci podręcznej lub folderu packages globalne dla komputera.</span><span class="sxs-lookup"><span data-stu-id="4864a-267">Clears or lists local NuGet resources such as http-request cache, temporary cache, or machine-wide global packages folder.</span></span>
[<span data-ttu-id="4864a-268">dotnet nuget push</span><span class="sxs-lookup"><span data-stu-id="4864a-268">dotnet nuget push</span></span>](dotnet-nuget-push.md) | <span data-ttu-id="4864a-269">Wypychanie pakietu do serwera i publikuje ją.</span><span class="sxs-lookup"><span data-stu-id="4864a-269">Pushes a package to the server and publishes it.</span></span>

### <a name="global-tools-commands"></a><span data-ttu-id="4864a-270">Polecenia narzędzia globalne</span><span class="sxs-lookup"><span data-stu-id="4864a-270">Global Tools commands</span></span>

<span data-ttu-id="4864a-271">[Narzędzia globalne .NET core](global-tools.md) są dostępne począwszy od zestawu SDK programu .NET Core 2.1.300:</span><span class="sxs-lookup"><span data-stu-id="4864a-271">[.NET Core Global Tools](global-tools.md) are available starting with .NET Core SDK 2.1.300:</span></span>

<span data-ttu-id="4864a-272">Polecenie</span><span class="sxs-lookup"><span data-stu-id="4864a-272">Command</span></span> | <span data-ttu-id="4864a-273">Funkcja</span><span class="sxs-lookup"><span data-stu-id="4864a-273">Function</span></span>
--- | ---
[<span data-ttu-id="4864a-274">Instalowanie narzędzi DotNet</span><span class="sxs-lookup"><span data-stu-id="4864a-274">dotnet tool install</span></span>](dotnet-tool-install.md) | <span data-ttu-id="4864a-275">Instaluje narzędzie globalne na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="4864a-275">Installs a Global Tool on your machine.</span></span>
[<span data-ttu-id="4864a-276">Lista narzędzi DotNet</span><span class="sxs-lookup"><span data-stu-id="4864a-276">dotnet tool list</span></span>](dotnet-tool-list.md) | <span data-ttu-id="4864a-277">Wyświetla wszystkie narzędzia globalne aktualnie zainstalowany domyślny katalog na komputerze lub w określonej ścieżce.</span><span class="sxs-lookup"><span data-stu-id="4864a-277">Lists all Global Tools currently installed in the default directory on your machine or in the specified path.</span></span>
[<span data-ttu-id="4864a-278">Odinstaluj narzędzie DotNet</span><span class="sxs-lookup"><span data-stu-id="4864a-278">dotnet tool uninstall</span></span>](dotnet-tool-uninstall.md) | <span data-ttu-id="4864a-279">Odinstalowuje narzędzie globalne z komputera.</span><span class="sxs-lookup"><span data-stu-id="4864a-279">Uninstalls a Global Tool from your machine.</span></span>
[<span data-ttu-id="4864a-280">Aktualizacja narzędzi DotNet</span><span class="sxs-lookup"><span data-stu-id="4864a-280">dotnet tool update</span></span>](dotnet-tool-update.md) | <span data-ttu-id="4864a-281">Aktualizuje narzędzie globalne na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="4864a-281">Updates a Global Tool on your machine.</span></span>

### <a name="additional-tools"></a><span data-ttu-id="4864a-282">Dodatkowe narzędzia</span><span class="sxs-lookup"><span data-stu-id="4864a-282">Additional tools</span></span>

<span data-ttu-id="4864a-283">Począwszy od programu .NET Core SDK 2.1.300, szereg narzędzi, które były dostępne tylko na projekt na podstawie przy użyciu `DotnetCliToolReference` są teraz dostępne jako część zestawu SDK .NET Core.</span><span class="sxs-lookup"><span data-stu-id="4864a-283">Starting with .NET Core SDK 2.1.300, a number of tools that were available only on a per project basis using `DotnetCliToolReference` are now available as part of the .NET Core SDK.</span></span> <span data-ttu-id="4864a-284">Narzędzia te obejmują:</span><span class="sxs-lookup"><span data-stu-id="4864a-284">These tools include:</span></span>

| <span data-ttu-id="4864a-285">Narzędzie</span><span class="sxs-lookup"><span data-stu-id="4864a-285">Tool</span></span>                                              | <span data-ttu-id="4864a-286">Funkcja</span><span class="sxs-lookup"><span data-stu-id="4864a-286">Function</span></span>                                                     |
| ------------------------------------------------- | ------------------------------------------------------------ |
| <span data-ttu-id="4864a-287">certyfikaty dla deweloperów</span><span class="sxs-lookup"><span data-stu-id="4864a-287">dev-certs</span></span>                                         | <span data-ttu-id="4864a-288">Tworzy i którymi zarządza programowanie certyfikatów.</span><span class="sxs-lookup"><span data-stu-id="4864a-288">Creates and manages development certificates.</span></span>                |
| [<span data-ttu-id="4864a-289">EF</span><span class="sxs-lookup"><span data-stu-id="4864a-289">ef</span></span>](/ef/core/miscellaneous/cli/dotnet)           | <span data-ttu-id="4864a-290">Entity Framework Core narzędzia wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="4864a-290">Entity Framework Core command-line tools.</span></span>                    |
| <span data-ttu-id="4864a-291">pamięć podręczna SQL</span><span class="sxs-lookup"><span data-stu-id="4864a-291">sql-cache</span></span>                                         | <span data-ttu-id="4864a-292">Narzędzia wiersza polecenia pamięci podręcznej programu SQL Server.</span><span class="sxs-lookup"><span data-stu-id="4864a-292">SQL Server cache command-line tools.</span></span>                         |
| [<span data-ttu-id="4864a-293">hasła użytkownika</span><span class="sxs-lookup"><span data-stu-id="4864a-293">user-secrets</span></span>](/aspnet/core/security/app-secrets) | <span data-ttu-id="4864a-294">Zarządza programowanie hasła użytkownika.</span><span class="sxs-lookup"><span data-stu-id="4864a-294">Manages development user secrets.</span></span>                            |
| [<span data-ttu-id="4864a-295">Czujki</span><span class="sxs-lookup"><span data-stu-id="4864a-295">watch</span></span>](/aspnet/core/tutorials/dotnet-watch)      | <span data-ttu-id="4864a-296">Uruchamia obserwatora pliku, który uruchamia polecenie zmianach plików.</span><span class="sxs-lookup"><span data-stu-id="4864a-296">Starts a file watcher that runs a command when files change.</span></span> |

<span data-ttu-id="4864a-297">Aby uzyskać więcej informacji na temat narzędzia wykonania `dotnet <tool-name> --help`.</span><span class="sxs-lookup"><span data-stu-id="4864a-297">For more information about each tool, execute `dotnet <tool-name> --help`.</span></span>

## <a name="examples"></a><span data-ttu-id="4864a-298">Przykłady</span><span class="sxs-lookup"><span data-stu-id="4864a-298">Examples</span></span>

<span data-ttu-id="4864a-299">Tworzy nową aplikację konsolową .NET Core:</span><span class="sxs-lookup"><span data-stu-id="4864a-299">Creates a new .NET Core console application:</span></span>

`dotnet new console`

<span data-ttu-id="4864a-300">Przywróć zależności dla danej aplikacji:</span><span class="sxs-lookup"><span data-stu-id="4864a-300">Restore dependencies for a given application:</span></span>

`dotnet restore`

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

<span data-ttu-id="4864a-301">Tworzenie projektu i jego zależności w podanym katalogu:</span><span class="sxs-lookup"><span data-stu-id="4864a-301">Build a project and its dependencies in a given directory:</span></span>

`dotnet build`

<span data-ttu-id="4864a-302">Uruchamianie aplikacji zależnych od framework o nazwie `myapp.dll`:</span><span class="sxs-lookup"><span data-stu-id="4864a-302">Run a framework-dependent app named `myapp.dll`:</span></span>

`dotnet myapp.dll`

## <a name="environment-variables"></a><span data-ttu-id="4864a-303">Zmienne środowiskowe</span><span class="sxs-lookup"><span data-stu-id="4864a-303">Environment variables</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="4864a-304">Oprogramowanie .NET core 2.1</span><span class="sxs-lookup"><span data-stu-id="4864a-304">.NET Core 2.1</span></span>](#tab/netcore21)

`DOTNET_PACKAGES`

<span data-ttu-id="4864a-305">Pakiet główny pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="4864a-305">The primary package cache.</span></span> <span data-ttu-id="4864a-306">Jeśli nie został ustawiony, domyślnie `$HOME/.nuget/packages` w systemie Unix lub `%HOME%\NuGet\Packages` w systemie Windows.</span><span class="sxs-lookup"><span data-stu-id="4864a-306">If not set, it defaults to `$HOME/.nuget/packages` on Unix or `%HOME%\NuGet\Packages` on Windows.</span></span>

`DOTNET_SERVICING`

<span data-ttu-id="4864a-307">Określa lokalizację obsługi indeksu jest używany przez hosta udostępnionych podczas ładowania środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="4864a-307">Specifies the location of the servicing index to use by the shared host when loading the runtime.</span></span>

`DOTNET_CLI_TELEMETRY_OPTOUT`

<span data-ttu-id="4864a-308">Określa, czy dane dotyczące użycia narzędzia .NET Core został zebrany i wysyłany do firmy Microsoft.</span><span class="sxs-lookup"><span data-stu-id="4864a-308">Specifies whether data about the .NET Core tools usage is collected and sent to Microsoft.</span></span> <span data-ttu-id="4864a-309">Ustaw `true` Aby zrezygnować z funkcji telemetrii (wartości `true`, `1`, lub `yes` akceptowane).</span><span class="sxs-lookup"><span data-stu-id="4864a-309">Set to `true` to opt-out of the telemetry feature (values `true`, `1`, or `yes` accepted).</span></span> <span data-ttu-id="4864a-310">W przeciwnym razie wartość `false` do uczestnictwa w funkcji telemetrii (wartości `false`, `0`, lub `no` akceptowane).</span><span class="sxs-lookup"><span data-stu-id="4864a-310">Otherwise, set to `false` to opt into the telemetry features (values `false`, `0`, or `no` accepted).</span></span> <span data-ttu-id="4864a-311">Jeśli nie jest ustawiona, wartością domyślną jest `false` i funkcja telemetrii jest aktywna.</span><span class="sxs-lookup"><span data-stu-id="4864a-311">If not set, the default is `false` and the telemetry feature is active.</span></span>

`DOTNET_MULTILEVEL_LOOKUP`

<span data-ttu-id="4864a-312">Określa, czy środowiska uruchomieniowego .NET Core, udostępnionych framework lub zestawu SDK są rozpoznane w globalnej lokalizacji.</span><span class="sxs-lookup"><span data-stu-id="4864a-312">Specifies whether .NET Core runtime, shared framework, or SDK are resolved from the global location.</span></span> <span data-ttu-id="4864a-313">Jeśli nie jest ustawiona, domyślne `true`.</span><span class="sxs-lookup"><span data-stu-id="4864a-313">If not set, it defaults to `true`.</span></span> <span data-ttu-id="4864a-314">Ustaw `false` rozwiązania z globalnej lokalizacji i mają odizolowane instalacji platformy .NET Core (wartości `0` lub `false` są akceptowane).</span><span class="sxs-lookup"><span data-stu-id="4864a-314">Set to `false` to not resolve from the global location and have isolated .NET Core installations (values `0` or `false` are accepted).</span></span> <span data-ttu-id="4864a-315">Aby uzyskać więcej informacji na temat wyszukiwania wielopoziomowe zobacz [wyszukiwania SharedFX wielopoziomowej](https://github.com/dotnet/core-setup/blob/master/Documentation/design-docs/multilevel-sharedfx-lookup.md).</span><span class="sxs-lookup"><span data-stu-id="4864a-315">For more information about multi-level lookup, see [Multi-level SharedFX Lookup](https://github.com/dotnet/core-setup/blob/master/Documentation/design-docs/multilevel-sharedfx-lookup.md).</span></span>

`DOTNET_ROLL_FORWARD_ON_NO_CANDIDATE_FX`

<span data-ttu-id="4864a-316">Wyłącza niewielkie wersji przenoszenia do przodu.</span><span class="sxs-lookup"><span data-stu-id="4864a-316">Disables minor version roll forward.</span></span> <span data-ttu-id="4864a-317">Aby uzyskać więcej informacji, zobacz [przekazywane dalej](../whats-new/dotnet-core-2-1.md#roll-forward).</span><span class="sxs-lookup"><span data-stu-id="4864a-317">For more information, see [Roll forward](../whats-new/dotnet-core-2-1.md#roll-forward).</span></span>

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="4864a-318">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="4864a-318">.NET Core 2.0</span></span>](#tab/netcore20)

`DOTNET_PACKAGES`

<span data-ttu-id="4864a-319">Pakiet główny pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="4864a-319">The primary package cache.</span></span> <span data-ttu-id="4864a-320">Jeśli nie został ustawiony, domyślnie `$HOME/.nuget/packages` w systemie Unix lub `%HOME%\NuGet\Packages` w systemie Windows.</span><span class="sxs-lookup"><span data-stu-id="4864a-320">If not set, it defaults to `$HOME/.nuget/packages` on Unix or `%HOME%\NuGet\Packages` on Windows.</span></span>

`DOTNET_SERVICING`

<span data-ttu-id="4864a-321">Określa lokalizację obsługi indeksu jest używany przez hosta udostępnionych podczas ładowania środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="4864a-321">Specifies the location of the servicing index to use by the shared host when loading the runtime.</span></span>

`DOTNET_CLI_TELEMETRY_OPTOUT`

<span data-ttu-id="4864a-322">Określa, czy dane dotyczące użycia narzędzia .NET Core został zebrany i wysyłany do firmy Microsoft.</span><span class="sxs-lookup"><span data-stu-id="4864a-322">Specifies whether data about the .NET Core tools usage is collected and sent to Microsoft.</span></span> <span data-ttu-id="4864a-323">Ustaw `true` Aby zrezygnować z funkcji telemetrii (wartości `true`, `1`, lub `yes` akceptowane).</span><span class="sxs-lookup"><span data-stu-id="4864a-323">Set to `true` to opt-out of the telemetry feature (values `true`, `1`, or `yes` accepted).</span></span> <span data-ttu-id="4864a-324">W przeciwnym razie wartość `false` do uczestnictwa w funkcji telemetrii (wartości `false`, `0`, lub `no` akceptowane).</span><span class="sxs-lookup"><span data-stu-id="4864a-324">Otherwise, set to `false` to opt into the telemetry features (values `false`, `0`, or `no` accepted).</span></span> <span data-ttu-id="4864a-325">Jeśli nie jest ustawiona, wartością domyślną jest `false` i funkcja telemetrii jest aktywna.</span><span class="sxs-lookup"><span data-stu-id="4864a-325">If not set, the default is `false` and the telemetry feature is active.</span></span>

`DOTNET_MULTILEVEL_LOOKUP`

<span data-ttu-id="4864a-326">Określa, czy środowiska uruchomieniowego .NET Core, udostępnionych framework lub zestawu SDK są rozpoznane w globalnej lokalizacji.</span><span class="sxs-lookup"><span data-stu-id="4864a-326">Specifies whether .NET Core runtime, shared framework, or SDK are resolved from the global location.</span></span> <span data-ttu-id="4864a-327">Jeśli nie jest ustawiona, domyślne `true`.</span><span class="sxs-lookup"><span data-stu-id="4864a-327">If not set, it defaults to `true`.</span></span> <span data-ttu-id="4864a-328">Ustaw `false` rozwiązania z globalnej lokalizacji i mają odizolowane instalacji platformy .NET Core (wartości `0` lub `false` są akceptowane).</span><span class="sxs-lookup"><span data-stu-id="4864a-328">Set to `false` to not resolve from the global location and have isolated .NET Core installations (values `0` or `false` are accepted).</span></span> <span data-ttu-id="4864a-329">Aby uzyskać więcej informacji na temat wyszukiwania wielopoziomowe zobacz [wyszukiwania SharedFX wielopoziomowej](https://github.com/dotnet/core-setup/blob/master/Documentation/design-docs/multilevel-sharedfx-lookup.md).</span><span class="sxs-lookup"><span data-stu-id="4864a-329">For more information about multi-level lookup, see [Multi-level SharedFX Lookup](https://github.com/dotnet/core-setup/blob/master/Documentation/design-docs/multilevel-sharedfx-lookup.md).</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="4864a-330">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="4864a-330">.NET Core 1.x</span></span>](#tab/netcore1x)

`DOTNET_PACKAGES`

<span data-ttu-id="4864a-331">Pakiet główny pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="4864a-331">The primary package cache.</span></span> <span data-ttu-id="4864a-332">Jeśli nie został ustawiony, domyślnie `$HOME/.nuget/packages` w systemie Unix lub `%HOME%\NuGet\Packages` w systemie Windows.</span><span class="sxs-lookup"><span data-stu-id="4864a-332">If not set, it defaults to `$HOME/.nuget/packages` on Unix or `%HOME%\NuGet\Packages` on Windows.</span></span>

`DOTNET_SERVICING`

<span data-ttu-id="4864a-333">Określa lokalizację obsługi indeksu jest używany przez hosta udostępnionych podczas ładowania środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="4864a-333">Specifies the location of the servicing index to use by the shared host when loading the runtime.</span></span>

`DOTNET_CLI_TELEMETRY_OPTOUT`

<span data-ttu-id="4864a-334">Określa, czy dane dotyczące użycia narzędzia .NET Core został zebrany i wysyłany do firmy Microsoft.</span><span class="sxs-lookup"><span data-stu-id="4864a-334">Specifies whether data about the .NET Core tools usage is collected and sent to Microsoft.</span></span> <span data-ttu-id="4864a-335">Ustaw `true` Aby zrezygnować z funkcji telemetrii (wartości `true`, `1`, lub `yes` akceptowane).</span><span class="sxs-lookup"><span data-stu-id="4864a-335">Set to `true` to opt-out of the telemetry feature (values `true`, `1`, or `yes` accepted).</span></span> <span data-ttu-id="4864a-336">W przeciwnym razie wartość `false` do uczestnictwa w funkcji telemetrii (wartości `false`, `0`, lub `no` akceptowane).</span><span class="sxs-lookup"><span data-stu-id="4864a-336">Otherwise, set to `false` to opt into the telemetry features (values `false`, `0`, or `no` accepted).</span></span> <span data-ttu-id="4864a-337">Jeśli nie jest ustawiona, wartością domyślną jest `false` i funkcja telemetrii jest aktywna.</span><span class="sxs-lookup"><span data-stu-id="4864a-337">If not set, the default is `false` and the telemetry feature is active.</span></span>

---
