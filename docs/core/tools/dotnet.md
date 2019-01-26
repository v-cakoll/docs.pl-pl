---
title: polecenia DotNet
description: Więcej informacji na temat polecenia dotnet (ogólny sterownik dla narzędzi interfejsu wiersza polecenia platformy .NET Core) i sposób jej użycia.
ms.date: 06/04/2018
ms.openlocfilehash: 53eb96ee6fe809b2e6e42eec4e7e9b5f7c5edf2a
ms.sourcegitcommit: d9a0071d0fd490ae006c816f78a563b9946e269a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "55066444"
---
# <a name="dotnet-command"></a><span data-ttu-id="3e68d-103">polecenia DotNet</span><span class="sxs-lookup"><span data-stu-id="3e68d-103">dotnet command</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="3e68d-104">Nazwa</span><span class="sxs-lookup"><span data-stu-id="3e68d-104">Name</span></span>

<span data-ttu-id="3e68d-105">`dotnet` — Narzędzie służące do zarządzania kodu źródłowego .NET i plikach binarnych.</span><span class="sxs-lookup"><span data-stu-id="3e68d-105">`dotnet` - A tool for managing .NET source code and binaries.</span></span>

## <a name="synopsis"></a><span data-ttu-id="3e68d-106">Streszczenie</span><span class="sxs-lookup"><span data-stu-id="3e68d-106">Synopsis</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="3e68d-107">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="3e68d-107">.NET Core 2.1</span></span>](#tab/netcore21)
```
dotnet [command] [arguments] [--additional-deps] [--additionalprobingpath] [-d|--diagnostics] [--fx-version]
    [-h|--help] [--info] [--list-runtimes] [--list-sdks] [--roll-forward-on-no-candidate-fx] [-v|--verbosity] [--version]
```
# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="3e68d-108">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="3e68d-108">.NET Core 2.0</span></span>](#tab/netcore20)
```
dotnet [command] [arguments] [--additional-deps] [--additionalprobingpath] [-d|--diagnostics]
    [--fx-version] [-h|--help] [--info] [--roll-forward-on-no-candidate-fx] [-v|--verbosity] [--version]
```
# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="3e68d-109">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="3e68d-109">.NET Core 1.x</span></span>](#tab/netcore1x)
```
dotnet [command] [arguments] [--additionalprobingpath] [-d|--diagnostics] [--fx-version]
    [-h|--help] [--info] [-v|--verbosity] [--version]
```
---

## <a name="description"></a><span data-ttu-id="3e68d-110">Opis</span><span class="sxs-lookup"><span data-stu-id="3e68d-110">Description</span></span>

<span data-ttu-id="3e68d-111">`dotnet` to narzędzie do zarządzania kodu źródłowego .NET i pliki binarne.</span><span class="sxs-lookup"><span data-stu-id="3e68d-111">`dotnet` is a tool for managing .NET source code and binaries.</span></span> <span data-ttu-id="3e68d-112">Udostępnia ona polecenia, które wykonują określone zadania, takie jak [ `dotnet build` ](dotnet-build.md) i [ `dotnet run` ](dotnet-run.md).</span><span class="sxs-lookup"><span data-stu-id="3e68d-112">It exposes commands that perform specific tasks, such as [`dotnet build`](dotnet-build.md) and [`dotnet run`](dotnet-run.md).</span></span> <span data-ttu-id="3e68d-113">Każde polecenie definiuje swój własny argumentów.</span><span class="sxs-lookup"><span data-stu-id="3e68d-113">Each command defines its own arguments.</span></span> <span data-ttu-id="3e68d-114">Typ `--help` zatwierdzając każde z nich do dostępu krótki opis dokumentacji pomocy.</span><span class="sxs-lookup"><span data-stu-id="3e68d-114">Type `--help` after each command to access brief help documentation.</span></span>

<span data-ttu-id="3e68d-115">`dotnet` może służyć do uruchamiania aplikacji, określając aplikacji biblioteki DLL, takie jak `dotnet myapp.dll`.</span><span class="sxs-lookup"><span data-stu-id="3e68d-115">`dotnet` can be used to run applications, by specifying an application DLL, such as `dotnet myapp.dll`.</span></span> <span data-ttu-id="3e68d-116">Zobacz [wdrażanie aplikacji .NET Core](../deploying/index.md) dla Aby dowiedzieć się więcej o opcjach wdrażania.</span><span class="sxs-lookup"><span data-stu-id="3e68d-116">See [.NET Core application deployment](../deploying/index.md) for to learn about deployment options.</span></span>

## <a name="options"></a><span data-ttu-id="3e68d-117">Opcje</span><span class="sxs-lookup"><span data-stu-id="3e68d-117">Options</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="3e68d-118">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="3e68d-118">.NET Core 2.1</span></span>](#tab/netcore21)

`--additional-deps <PATH>`

<span data-ttu-id="3e68d-119">Ścieżka do dodatkowych *deps.json* pliku.</span><span class="sxs-lookup"><span data-stu-id="3e68d-119">Path to additional *deps.json* file.</span></span>

`--additionalprobingpath <PATH>`

<span data-ttu-id="3e68d-120">Ścieżki zawierające sondowania zasad i zestawy do sondowania.</span><span class="sxs-lookup"><span data-stu-id="3e68d-120">Path containing probing policy and assemblies to probe.</span></span>

`-d|--diagnostics`

<span data-ttu-id="3e68d-121">Umożliwia diagnostyczne dane wyjściowe.</span><span class="sxs-lookup"><span data-stu-id="3e68d-121">Enables diagnostic output.</span></span>

`--fx-version <VERSION>`

<span data-ttu-id="3e68d-122">Wersja środowiska uruchomieniowego .NET Core do użycia, aby uruchomić aplikację.</span><span class="sxs-lookup"><span data-stu-id="3e68d-122">Version of the .NET Core runtime to use to run the application.</span></span>

`-h|--help`

<span data-ttu-id="3e68d-123">Wyświetla dokumentację dotyczącą danego polecenia, takie jak `dotnet build --help`.</span><span class="sxs-lookup"><span data-stu-id="3e68d-123">Prints out documentation for a given command, such as `dotnet build --help`.</span></span> <span data-ttu-id="3e68d-124">`dotnet --help` Wyświetla listę dostępnych poleceń.</span><span class="sxs-lookup"><span data-stu-id="3e68d-124">`dotnet --help` prints a list of available commands.</span></span>

`--info`

<span data-ttu-id="3e68d-125">Drukuje szczegółowe informacje dotyczące instalacji platformy .NET Core i środowiska maszyny, takich jak bieżący system operacyjny i zatwierdzenie SHA wersji platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="3e68d-125">Prints out detailed information about a .NET Core installation and the machine environment, such as the current operating system, and commit SHA of the .NET Core version.</span></span>

`--list-runtimes`

<span data-ttu-id="3e68d-126">Wyświetla zainstalowane środowiska uruchomieniowe platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="3e68d-126">Displays the installed .NET Core runtimes.</span></span>

`--list-sdks`

<span data-ttu-id="3e68d-127">Wyświetla zainstalowanych zestawów .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="3e68d-127">Displays the installed .NET Core SDKs.</span></span>

`--roll-forward-on-no-candidate-fx <N>`

<span data-ttu-id="3e68d-128">Definiuje zachowanie, gdy wymaganej struktury udostępnionego nie jest dostępna.</span><span class="sxs-lookup"><span data-stu-id="3e68d-128">Defines behavior when the required shared framework is not available.</span></span> <span data-ttu-id="3e68d-129">`N` może być:</span><span class="sxs-lookup"><span data-stu-id="3e68d-129">`N` can be:</span></span>
 * <span data-ttu-id="3e68d-130">`0` -Wyłącz nawet podverze przenoszenia do przodu.</span><span class="sxs-lookup"><span data-stu-id="3e68d-130">`0` - Disable even minor version roll forward.</span></span>
 * <span data-ttu-id="3e68d-131">`1` -Uaktualniane w wersji pomocniczej, ale nie w wersji głównej.</span><span class="sxs-lookup"><span data-stu-id="3e68d-131">`1` - Roll forward on minor version, but not on major version.</span></span> <span data-ttu-id="3e68d-132">Jest to zachowanie domyślne.</span><span class="sxs-lookup"><span data-stu-id="3e68d-132">This is the default behavior.</span></span>
 * <span data-ttu-id="3e68d-133">`2` -Uaktualniane na wersje pomocnicze, jak i głównej.</span><span class="sxs-lookup"><span data-stu-id="3e68d-133">`2` - Roll forward on minor and major versions.</span></span>

 <span data-ttu-id="3e68d-134">Aby uzyskać więcej informacji, zobacz [uaktualniane](../whats-new/dotnet-core-2-1.md#roll-forward).</span><span class="sxs-lookup"><span data-stu-id="3e68d-134">For more information, see [Roll forward](../whats-new/dotnet-core-2-1.md#roll-forward).</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="3e68d-135">Ustawia poziom szczegółowości polecenia.</span><span class="sxs-lookup"><span data-stu-id="3e68d-135">Sets the verbosity level of the command.</span></span> <span data-ttu-id="3e68d-136">Dozwolone wartości to `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, i `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="3e68d-136">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="3e68d-137">Nie jest obsługiwana w każdym poleceniu; zobacz stronę określone polecenie, aby określić, jeśli ta opcja jest dostępna.</span><span class="sxs-lookup"><span data-stu-id="3e68d-137">Not supported in every command; see specific command page to determine if this option is available.</span></span>

`--version`

<span data-ttu-id="3e68d-138">Drukuje wersję zestawu .NET Core SDK w użyciu.</span><span class="sxs-lookup"><span data-stu-id="3e68d-138">Prints out the version of the .NET Core SDK in use.</span></span>

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="3e68d-139">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="3e68d-139">.NET Core 2.0</span></span>](#tab/netcore20)

`--additional-deps <PATH>`

<span data-ttu-id="3e68d-140">Ścieżka do dodatkowych *deps.json* pliku.</span><span class="sxs-lookup"><span data-stu-id="3e68d-140">Path to additional *deps.json* file.</span></span>

`--additionalprobingpath <PATH>`

<span data-ttu-id="3e68d-141">Ścieżki zawierające sondowania zasad i zestawy do sondowania.</span><span class="sxs-lookup"><span data-stu-id="3e68d-141">Path containing probing policy and assemblies to probe.</span></span>

`-d|--diagnostics`

<span data-ttu-id="3e68d-142">Umożliwia diagnostyczne dane wyjściowe.</span><span class="sxs-lookup"><span data-stu-id="3e68d-142">Enables diagnostic output.</span></span>

`--fx-version <VERSION>`

<span data-ttu-id="3e68d-143">Wersja środowiska uruchomieniowego .NET Core do użycia, aby uruchomić aplikację.</span><span class="sxs-lookup"><span data-stu-id="3e68d-143">Version of the .NET Core runtime to use to run the application.</span></span>

`-h|--help`

<span data-ttu-id="3e68d-144">Wyświetla dokumentację dotyczącą danego polecenia, takie jak `dotnet build --help`.</span><span class="sxs-lookup"><span data-stu-id="3e68d-144">Prints out documentation for a given command, such as `dotnet build --help`.</span></span> <span data-ttu-id="3e68d-145">`dotnet --help` Wyświetla listę dostępnych poleceń.</span><span class="sxs-lookup"><span data-stu-id="3e68d-145">`dotnet --help` prints a list of available commands.</span></span>

`--info`

<span data-ttu-id="3e68d-146">Drukuje szczegółowe informacje dotyczące instalacji platformy .NET Core i środowiska maszyny, takich jak bieżący system operacyjny i zatwierdzenie SHA wersji platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="3e68d-146">Prints out detailed information about a .NET Core installation and the machine environment, such as the current operating system, and commit SHA of the .NET Core version.</span></span>

`--roll-forward-on-no-candidate-fx`

 <span data-ttu-id="3e68d-147">Wyłącza wersja pomocnicza przenoszenie do przodu, jeśli ustawiono `0`.</span><span class="sxs-lookup"><span data-stu-id="3e68d-147">Disables minor version roll forward, if set to `0`.</span></span> <span data-ttu-id="3e68d-148">Aby uzyskać więcej informacji, zobacz [uaktualniane](../whats-new/dotnet-core-2-1.md#roll-forward).</span><span class="sxs-lookup"><span data-stu-id="3e68d-148">For more information, see [Roll forward](../whats-new/dotnet-core-2-1.md#roll-forward).</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="3e68d-149">Ustawia poziom szczegółowości polecenia.</span><span class="sxs-lookup"><span data-stu-id="3e68d-149">Sets the verbosity level of the command.</span></span> <span data-ttu-id="3e68d-150">Dozwolone wartości to `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, i `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="3e68d-150">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="3e68d-151">Nie jest obsługiwana w każdym poleceniu; zobacz stronę określone polecenie, aby określić, jeśli ta opcja jest dostępna.</span><span class="sxs-lookup"><span data-stu-id="3e68d-151">Not supported in every command; see specific command page to determine if this option is available.</span></span>

`--version`

<span data-ttu-id="3e68d-152">Drukuje wersję zestawu .NET Core SDK w użyciu.</span><span class="sxs-lookup"><span data-stu-id="3e68d-152">Prints out the version of the .NET Core SDK in use.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="3e68d-153">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="3e68d-153">.NET Core 1.x</span></span>](#tab/netcore1x)

`--additionalprobingpath <PATH>`

<span data-ttu-id="3e68d-154">Ścieżki zawierające sondowania zasad i zestawy do sondowania.</span><span class="sxs-lookup"><span data-stu-id="3e68d-154">Path containing probing policy and assemblies to probe.</span></span>

`-d|--diagnostics`

<span data-ttu-id="3e68d-155">Umożliwia diagnostyczne dane wyjściowe.</span><span class="sxs-lookup"><span data-stu-id="3e68d-155">Enables diagnostic output.</span></span>

`--fx-version <VERSION>`

<span data-ttu-id="3e68d-156">Wersja środowiska uruchomieniowego .NET Core do użycia, aby uruchomić aplikację.</span><span class="sxs-lookup"><span data-stu-id="3e68d-156">Version of the .NET Core runtime to use to run the application.</span></span>

`-h|--help`

<span data-ttu-id="3e68d-157">Wyświetla dokumentację dotyczącą danego polecenia, takie jak `dotnet build --help`.</span><span class="sxs-lookup"><span data-stu-id="3e68d-157">Prints out documentation for a given command, such as `dotnet build --help`.</span></span> <span data-ttu-id="3e68d-158">`dotnet --help` Wyświetla listę dostępnych poleceń.</span><span class="sxs-lookup"><span data-stu-id="3e68d-158">`dotnet --help` prints a list of available commands.</span></span>

`--info`

<span data-ttu-id="3e68d-159">Drukuje szczegółowe informacje dotyczące instalacji platformy .NET Core i środowiska maszyny, takich jak bieżący system operacyjny i zatwierdzenie SHA wersji platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="3e68d-159">Prints out detailed information about a .NET Core installation and the machine environment, such as the current operating system, and commit SHA of the .NET Core version.</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="3e68d-160">Ustawia poziom szczegółowości polecenia.</span><span class="sxs-lookup"><span data-stu-id="3e68d-160">Sets the verbosity level of the command.</span></span> <span data-ttu-id="3e68d-161">Dozwolone wartości to `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, i `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="3e68d-161">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="3e68d-162">Nie jest obsługiwana w każdym poleceniu; zobacz stronę określone polecenie, aby określić, jeśli ta opcja jest dostępna.</span><span class="sxs-lookup"><span data-stu-id="3e68d-162">Not supported in every command; see specific command page to determine if this option is available.</span></span>

`--version`

<span data-ttu-id="3e68d-163">Drukuje wersję zestawu .NET Core SDK w użyciu.</span><span class="sxs-lookup"><span data-stu-id="3e68d-163">Prints out the version of the .NET Core SDK in use.</span></span>

---

## <a name="dotnet-commands"></a><span data-ttu-id="3e68d-164">polecenia DotNet</span><span class="sxs-lookup"><span data-stu-id="3e68d-164">dotnet commands</span></span>

### <a name="general"></a><span data-ttu-id="3e68d-165">Ogólne</span><span class="sxs-lookup"><span data-stu-id="3e68d-165">General</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="3e68d-166">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="3e68d-166">.NET Core 2.1</span></span>](#tab/netcore21)

| <span data-ttu-id="3e68d-167">Polecenie</span><span class="sxs-lookup"><span data-stu-id="3e68d-167">Command</span></span>                                       | <span data-ttu-id="3e68d-168">Funkcja</span><span class="sxs-lookup"><span data-stu-id="3e68d-168">Function</span></span>                                                            |
| --------------------------------------------- | ------------------------------------------------------------------- |
| [<span data-ttu-id="3e68d-169">dotnet build</span><span class="sxs-lookup"><span data-stu-id="3e68d-169">dotnet build</span></span>](dotnet-build.md)               | <span data-ttu-id="3e68d-170">Tworzy aplikację .NET Core.</span><span class="sxs-lookup"><span data-stu-id="3e68d-170">Builds a .NET Core application.</span></span>                                     |
| [<span data-ttu-id="3e68d-171">dotnet build-server</span><span class="sxs-lookup"><span data-stu-id="3e68d-171">dotnet build-server</span></span>](dotnet-build-server.md) | <span data-ttu-id="3e68d-172">Wchodzi w interakcję z serwerami, uruchomione przez kompilację.</span><span class="sxs-lookup"><span data-stu-id="3e68d-172">Interacts with servers started by a build.</span></span>                          |
| [<span data-ttu-id="3e68d-173">dotnet clean</span><span class="sxs-lookup"><span data-stu-id="3e68d-173">dotnet clean</span></span>](dotnet-clean.md)               | <span data-ttu-id="3e68d-174">Czysta kompilacja danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="3e68d-174">Clean build outputs.</span></span>                                                |
| [<span data-ttu-id="3e68d-175">dotnet help</span><span class="sxs-lookup"><span data-stu-id="3e68d-175">dotnet help</span></span>](dotnet-help.md)                 | <span data-ttu-id="3e68d-176">Zawiera bardziej szczegółowe dokumentację online dla polecenia.</span><span class="sxs-lookup"><span data-stu-id="3e68d-176">Shows more detailed documentation online for the command.</span></span>           |
| [<span data-ttu-id="3e68d-177">dotnet migrate</span><span class="sxs-lookup"><span data-stu-id="3e68d-177">dotnet migrate</span></span>](dotnet-migrate.md)           | <span data-ttu-id="3e68d-178">Prawidłowy projekt w wersji 2 jest migrowana do projektu .NET Core SDK 1.0.</span><span class="sxs-lookup"><span data-stu-id="3e68d-178">Migrates a valid Preview 2 project to a .NET Core SDK 1.0 project.</span></span>  |
| [<span data-ttu-id="3e68d-179">dotnet msbuild</span><span class="sxs-lookup"><span data-stu-id="3e68d-179">dotnet msbuild</span></span>](dotnet-msbuild.md)           | <span data-ttu-id="3e68d-180">Zapewnia dostęp do wiersza polecenia programu MSBuild.</span><span class="sxs-lookup"><span data-stu-id="3e68d-180">Provides access to the MSBuild command line.</span></span>                        |
| [<span data-ttu-id="3e68d-181">dotnet new</span><span class="sxs-lookup"><span data-stu-id="3e68d-181">dotnet new</span></span>](dotnet-new.md)                   | <span data-ttu-id="3e68d-182">Inicjuje C# lub F# projektu dla danego szablonu.</span><span class="sxs-lookup"><span data-stu-id="3e68d-182">Initializes a C# or F# project for a given template.</span></span>                |
| [<span data-ttu-id="3e68d-183">dotnet pack</span><span class="sxs-lookup"><span data-stu-id="3e68d-183">dotnet pack</span></span>](dotnet-pack.md)                 | <span data-ttu-id="3e68d-184">Tworzy pakiet NuGet kodu.</span><span class="sxs-lookup"><span data-stu-id="3e68d-184">Creates a NuGet package of your code.</span></span>                               |
| [<span data-ttu-id="3e68d-185">dotnet publish</span><span class="sxs-lookup"><span data-stu-id="3e68d-185">dotnet publish</span></span>](dotnet-publish.md)           | <span data-ttu-id="3e68d-186">Publikuje aplikacji autonomicznej .NET framework-zależnych od ustawień lokalnych lub niezależna.</span><span class="sxs-lookup"><span data-stu-id="3e68d-186">Publishes a .NET framework-dependent or self-contained application.</span></span> |
| [<span data-ttu-id="3e68d-187">dotnet restore</span><span class="sxs-lookup"><span data-stu-id="3e68d-187">dotnet restore</span></span>](dotnet-restore.md)           | <span data-ttu-id="3e68d-188">Przywraca zależności dla danej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="3e68d-188">Restores the dependencies for a given application.</span></span>                  |
| [<span data-ttu-id="3e68d-189">dotnet run</span><span class="sxs-lookup"><span data-stu-id="3e68d-189">dotnet run</span></span>](dotnet-run.md)                   | <span data-ttu-id="3e68d-190">Ze źródła do uruchamiania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="3e68d-190">Runs the application from source.</span></span>                                   |
| [<span data-ttu-id="3e68d-191">dotnet sln</span><span class="sxs-lookup"><span data-stu-id="3e68d-191">dotnet sln</span></span>](dotnet-sln.md)                   | <span data-ttu-id="3e68d-192">Opcje służące do dodawania, usuwania i wyświetlić listę projektów w pliku rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="3e68d-192">Options to add, remove, and list projects in a solution file.</span></span>       |
| [<span data-ttu-id="3e68d-193">dotnet store</span><span class="sxs-lookup"><span data-stu-id="3e68d-193">dotnet store</span></span>](dotnet-store.md)               | <span data-ttu-id="3e68d-194">Przechowuje zestawy w Magazyn pakietu środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="3e68d-194">Stores assemblies in the runtime package store.</span></span>                     |
| [<span data-ttu-id="3e68d-195">dotnet test</span><span class="sxs-lookup"><span data-stu-id="3e68d-195">dotnet test</span></span>](dotnet-test.md)                 | <span data-ttu-id="3e68d-196">Uruchamia testy za pomocą narzędzia test runner.</span><span class="sxs-lookup"><span data-stu-id="3e68d-196">Runs tests using a test runner.</span></span>                                     |

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="3e68d-197">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="3e68d-197">.NET Core 2.0</span></span>](#tab/netcore20)

| <span data-ttu-id="3e68d-198">Polecenie</span><span class="sxs-lookup"><span data-stu-id="3e68d-198">Command</span></span>                             | <span data-ttu-id="3e68d-199">Funkcja</span><span class="sxs-lookup"><span data-stu-id="3e68d-199">Function</span></span>                                                            |
| ----------------------------------- | ------------------------------------------------------------------- |
| [<span data-ttu-id="3e68d-200">dotnet build</span><span class="sxs-lookup"><span data-stu-id="3e68d-200">dotnet build</span></span>](dotnet-build.md)     | <span data-ttu-id="3e68d-201">Tworzy aplikację .NET Core.</span><span class="sxs-lookup"><span data-stu-id="3e68d-201">Builds a .NET Core application.</span></span>                                     |
| [<span data-ttu-id="3e68d-202">dotnet clean</span><span class="sxs-lookup"><span data-stu-id="3e68d-202">dotnet clean</span></span>](dotnet-clean.md)     | <span data-ttu-id="3e68d-203">Czysta kompilacja danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="3e68d-203">Clean build outputs.</span></span>                                              |
| [<span data-ttu-id="3e68d-204">dotnet help</span><span class="sxs-lookup"><span data-stu-id="3e68d-204">dotnet help</span></span>](dotnet-help.md)       | <span data-ttu-id="3e68d-205">Zawiera bardziej szczegółowe dokumentację online dla polecenia.</span><span class="sxs-lookup"><span data-stu-id="3e68d-205">Shows more detailed documentation online for the command.</span></span>           |
| [<span data-ttu-id="3e68d-206">dotnet migrate</span><span class="sxs-lookup"><span data-stu-id="3e68d-206">dotnet migrate</span></span>](dotnet-migrate.md) | <span data-ttu-id="3e68d-207">Prawidłowy projekt w wersji 2 jest migrowana do projektu .NET Core SDK 1.0.</span><span class="sxs-lookup"><span data-stu-id="3e68d-207">Migrates a valid Preview 2 project to a .NET Core SDK 1.0 project.</span></span>  |
| [<span data-ttu-id="3e68d-208">dotnet msbuild</span><span class="sxs-lookup"><span data-stu-id="3e68d-208">dotnet msbuild</span></span>](dotnet-msbuild.md) | <span data-ttu-id="3e68d-209">Zapewnia dostęp do wiersza polecenia programu MSBuild.</span><span class="sxs-lookup"><span data-stu-id="3e68d-209">Provides access to the MSBuild command line.</span></span>                        |
| [<span data-ttu-id="3e68d-210">dotnet new</span><span class="sxs-lookup"><span data-stu-id="3e68d-210">dotnet new</span></span>](dotnet-new.md)         | <span data-ttu-id="3e68d-211">Inicjuje C# lub F# projektu dla danego szablonu.</span><span class="sxs-lookup"><span data-stu-id="3e68d-211">Initializes a C# or F# project for a given template.</span></span>                |
| [<span data-ttu-id="3e68d-212">dotnet pack</span><span class="sxs-lookup"><span data-stu-id="3e68d-212">dotnet pack</span></span>](dotnet-pack.md)       | <span data-ttu-id="3e68d-213">Tworzy pakiet NuGet kodu.</span><span class="sxs-lookup"><span data-stu-id="3e68d-213">Creates a NuGet package of your code.</span></span>                               |
| [<span data-ttu-id="3e68d-214">dotnet publish</span><span class="sxs-lookup"><span data-stu-id="3e68d-214">dotnet publish</span></span>](dotnet-publish.md) | <span data-ttu-id="3e68d-215">Publikuje aplikacji autonomicznej .NET framework-zależnych od ustawień lokalnych lub niezależna.</span><span class="sxs-lookup"><span data-stu-id="3e68d-215">Publishes a .NET framework-dependent or self-contained application.</span></span> |
| [<span data-ttu-id="3e68d-216">dotnet restore</span><span class="sxs-lookup"><span data-stu-id="3e68d-216">dotnet restore</span></span>](dotnet-restore.md) | <span data-ttu-id="3e68d-217">Przywraca zależności dla danej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="3e68d-217">Restores the dependencies for a given application.</span></span>                  |
| [<span data-ttu-id="3e68d-218">dotnet run</span><span class="sxs-lookup"><span data-stu-id="3e68d-218">dotnet run</span></span>](dotnet-run.md)         | <span data-ttu-id="3e68d-219">Ze źródła do uruchamiania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="3e68d-219">Runs the application from source.</span></span>                                   |
| [<span data-ttu-id="3e68d-220">dotnet sln</span><span class="sxs-lookup"><span data-stu-id="3e68d-220">dotnet sln</span></span>](dotnet-sln.md)         | <span data-ttu-id="3e68d-221">Opcje służące do dodawania, usuwania i wyświetlić listę projektów w pliku rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="3e68d-221">Options to add, remove, and list projects in a solution file.</span></span>       |
| [<span data-ttu-id="3e68d-222">dotnet store</span><span class="sxs-lookup"><span data-stu-id="3e68d-222">dotnet store</span></span>](dotnet-store.md)     | <span data-ttu-id="3e68d-223">Przechowuje zestawy w Magazyn pakietu środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="3e68d-223">Stores assemblies in the runtime package store.</span></span>                     |
| [<span data-ttu-id="3e68d-224">dotnet test</span><span class="sxs-lookup"><span data-stu-id="3e68d-224">dotnet test</span></span>](dotnet-test.md)       | <span data-ttu-id="3e68d-225">Uruchamia testy za pomocą narzędzia test runner.</span><span class="sxs-lookup"><span data-stu-id="3e68d-225">Runs tests using a test runner.</span></span>                                     |

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="3e68d-226">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="3e68d-226">.NET Core 1.x</span></span>](#tab/netcore1x)

| <span data-ttu-id="3e68d-227">Polecenie</span><span class="sxs-lookup"><span data-stu-id="3e68d-227">Command</span></span>                             | <span data-ttu-id="3e68d-228">Funkcja</span><span class="sxs-lookup"><span data-stu-id="3e68d-228">Function</span></span>                                                            |
| ----------------------------------- | ------------------------------------------------------------------- |
| [<span data-ttu-id="3e68d-229">dotnet build</span><span class="sxs-lookup"><span data-stu-id="3e68d-229">dotnet build</span></span>](dotnet-build.md)     | <span data-ttu-id="3e68d-230">Tworzy aplikację .NET Core.</span><span class="sxs-lookup"><span data-stu-id="3e68d-230">Builds a .NET Core application.</span></span>                                     |
| [<span data-ttu-id="3e68d-231">dotnet clean</span><span class="sxs-lookup"><span data-stu-id="3e68d-231">dotnet clean</span></span>](dotnet-clean.md)     | <span data-ttu-id="3e68d-232">Czysta kompilacja danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="3e68d-232">Clean build outputs.</span></span>                                              |
| [<span data-ttu-id="3e68d-233">dotnet migrate</span><span class="sxs-lookup"><span data-stu-id="3e68d-233">dotnet migrate</span></span>](dotnet-migrate.md) | <span data-ttu-id="3e68d-234">Prawidłowy projekt w wersji 2 jest migrowana do projektu .NET Core SDK 1.0.</span><span class="sxs-lookup"><span data-stu-id="3e68d-234">Migrates a valid Preview 2 project to a .NET Core SDK 1.0 project.</span></span>  |
| [<span data-ttu-id="3e68d-235">dotnet msbuild</span><span class="sxs-lookup"><span data-stu-id="3e68d-235">dotnet msbuild</span></span>](dotnet-msbuild.md) | <span data-ttu-id="3e68d-236">Zapewnia dostęp do wiersza polecenia programu MSBuild.</span><span class="sxs-lookup"><span data-stu-id="3e68d-236">Provides access to the MSBuild command line.</span></span>                        |
| [<span data-ttu-id="3e68d-237">dotnet new</span><span class="sxs-lookup"><span data-stu-id="3e68d-237">dotnet new</span></span>](dotnet-new.md)         | <span data-ttu-id="3e68d-238">Inicjuje C# lub F# projektu dla danego szablonu.</span><span class="sxs-lookup"><span data-stu-id="3e68d-238">Initializes a C# or F# project for a given template.</span></span>                |
| [<span data-ttu-id="3e68d-239">dotnet pack</span><span class="sxs-lookup"><span data-stu-id="3e68d-239">dotnet pack</span></span>](dotnet-pack.md)       | <span data-ttu-id="3e68d-240">Tworzy pakiet NuGet kodu.</span><span class="sxs-lookup"><span data-stu-id="3e68d-240">Creates a NuGet package of your code.</span></span>                               |
| [<span data-ttu-id="3e68d-241">dotnet publish</span><span class="sxs-lookup"><span data-stu-id="3e68d-241">dotnet publish</span></span>](dotnet-publish.md) | <span data-ttu-id="3e68d-242">Publikuje aplikacji autonomicznej .NET framework-zależnych od ustawień lokalnych lub niezależna.</span><span class="sxs-lookup"><span data-stu-id="3e68d-242">Publishes a .NET framework-dependent or self-contained application.</span></span> |
| [<span data-ttu-id="3e68d-243">dotnet restore</span><span class="sxs-lookup"><span data-stu-id="3e68d-243">dotnet restore</span></span>](dotnet-restore.md) | <span data-ttu-id="3e68d-244">Przywraca zależności dla danej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="3e68d-244">Restores the dependencies for a given application.</span></span>                  |
| [<span data-ttu-id="3e68d-245">dotnet run</span><span class="sxs-lookup"><span data-stu-id="3e68d-245">dotnet run</span></span>](dotnet-run.md)         | <span data-ttu-id="3e68d-246">Ze źródła do uruchamiania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="3e68d-246">Runs the application from source.</span></span>                                   |
| [<span data-ttu-id="3e68d-247">dotnet sln</span><span class="sxs-lookup"><span data-stu-id="3e68d-247">dotnet sln</span></span>](dotnet-sln.md)         | <span data-ttu-id="3e68d-248">Opcje służące do dodawania, usuwania i wyświetlić listę projektów w pliku rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="3e68d-248">Options to add, remove, and list projects in a solution file.</span></span>       |
| [<span data-ttu-id="3e68d-249">dotnet test</span><span class="sxs-lookup"><span data-stu-id="3e68d-249">dotnet test</span></span>](dotnet-test.md)       | <span data-ttu-id="3e68d-250">Uruchamia testy za pomocą narzędzia test runner.</span><span class="sxs-lookup"><span data-stu-id="3e68d-250">Runs tests using a test runner.</span></span>                                     |

---

### <a name="project-references"></a><span data-ttu-id="3e68d-251">Odwołania do projektu</span><span class="sxs-lookup"><span data-stu-id="3e68d-251">Project references</span></span>

<span data-ttu-id="3e68d-252">Polecenie</span><span class="sxs-lookup"><span data-stu-id="3e68d-252">Command</span></span> | <span data-ttu-id="3e68d-253">Funkcja</span><span class="sxs-lookup"><span data-stu-id="3e68d-253">Function</span></span>
--- | ---
[<span data-ttu-id="3e68d-254">dotnet add reference</span><span class="sxs-lookup"><span data-stu-id="3e68d-254">dotnet add reference</span></span>](dotnet-add-reference.md) | <span data-ttu-id="3e68d-255">Dodaje odwołanie do projektu.</span><span class="sxs-lookup"><span data-stu-id="3e68d-255">Adds a project reference.</span></span>
[<span data-ttu-id="3e68d-256">dotnet list reference</span><span class="sxs-lookup"><span data-stu-id="3e68d-256">dotnet list reference</span></span>](dotnet-list-reference.md) | <span data-ttu-id="3e68d-257">Wyświetla listę odwołań do projektu.</span><span class="sxs-lookup"><span data-stu-id="3e68d-257">Lists project references.</span></span>
[<span data-ttu-id="3e68d-258">dotnet remove reference</span><span class="sxs-lookup"><span data-stu-id="3e68d-258">dotnet remove reference</span></span>](dotnet-remove-reference.md) | <span data-ttu-id="3e68d-259">Usuwa odwołanie do projektu.</span><span class="sxs-lookup"><span data-stu-id="3e68d-259">Removes a project reference.</span></span>

### <a name="nuget-packages"></a><span data-ttu-id="3e68d-260">Pakiety NuGet</span><span class="sxs-lookup"><span data-stu-id="3e68d-260">NuGet packages</span></span>

<span data-ttu-id="3e68d-261">Polecenie</span><span class="sxs-lookup"><span data-stu-id="3e68d-261">Command</span></span> | <span data-ttu-id="3e68d-262">Funkcja</span><span class="sxs-lookup"><span data-stu-id="3e68d-262">Function</span></span>
--- | ---
[<span data-ttu-id="3e68d-263">dotnet add package</span><span class="sxs-lookup"><span data-stu-id="3e68d-263">dotnet add package</span></span>](dotnet-add-package.md) | <span data-ttu-id="3e68d-264">Dodaje pakiet NuGet.</span><span class="sxs-lookup"><span data-stu-id="3e68d-264">Adds a NuGet package.</span></span>
[<span data-ttu-id="3e68d-265">dotnet remove package</span><span class="sxs-lookup"><span data-stu-id="3e68d-265">dotnet remove package</span></span>](dotnet-remove-package.md) | <span data-ttu-id="3e68d-266">Usuwa pakiet NuGet.</span><span class="sxs-lookup"><span data-stu-id="3e68d-266">Removes a NuGet package.</span></span>

### <a name="nuget-commands"></a><span data-ttu-id="3e68d-267">Polecenia NuGet</span><span class="sxs-lookup"><span data-stu-id="3e68d-267">NuGet commands</span></span>

<span data-ttu-id="3e68d-268">Polecenie</span><span class="sxs-lookup"><span data-stu-id="3e68d-268">Command</span></span> | <span data-ttu-id="3e68d-269">Funkcja</span><span class="sxs-lookup"><span data-stu-id="3e68d-269">Function</span></span>
--- | ---
[<span data-ttu-id="3e68d-270">dotnet nuget delete</span><span class="sxs-lookup"><span data-stu-id="3e68d-270">dotnet nuget delete</span></span>](dotnet-nuget-delete.md) | <span data-ttu-id="3e68d-271">Usuwa lub unlists pakietu z serwera.</span><span class="sxs-lookup"><span data-stu-id="3e68d-271">Deletes or unlists a package from the server.</span></span>
[<span data-ttu-id="3e68d-272">dotnet nuget locals</span><span class="sxs-lookup"><span data-stu-id="3e68d-272">dotnet nuget locals</span></span>](dotnet-nuget-locals.md) | <span data-ttu-id="3e68d-273">Usuwa lub wyświetla ich listę zasobów lokalnych NuGet, takie jak pamięć podręczna żądań http, tymczasowej pamięci podręcznej lub folder komputera globalnymi pakietami.</span><span class="sxs-lookup"><span data-stu-id="3e68d-273">Clears or lists local NuGet resources such as http-request cache, temporary cache, or machine-wide global packages folder.</span></span>
[<span data-ttu-id="3e68d-274">dotnet nuget push</span><span class="sxs-lookup"><span data-stu-id="3e68d-274">dotnet nuget push</span></span>](dotnet-nuget-push.md) | <span data-ttu-id="3e68d-275">Wypychanie pakietu do serwera i publikuje go.</span><span class="sxs-lookup"><span data-stu-id="3e68d-275">Pushes a package to the server and publishes it.</span></span>

### <a name="global-tools-commands"></a><span data-ttu-id="3e68d-276">Polecenia narzędzia globalne</span><span class="sxs-lookup"><span data-stu-id="3e68d-276">Global Tools commands</span></span>

<span data-ttu-id="3e68d-277">[Narzędzia programu .NET core globalnego](global-tools.md) są dostępne, począwszy od programu .NET Core SDK 2.1.300:</span><span class="sxs-lookup"><span data-stu-id="3e68d-277">[.NET Core Global Tools](global-tools.md) are available starting with .NET Core SDK 2.1.300:</span></span>

<span data-ttu-id="3e68d-278">Polecenie</span><span class="sxs-lookup"><span data-stu-id="3e68d-278">Command</span></span> | <span data-ttu-id="3e68d-279">Funkcja</span><span class="sxs-lookup"><span data-stu-id="3e68d-279">Function</span></span>
--- | ---
[<span data-ttu-id="3e68d-280">dotnet tool install</span><span class="sxs-lookup"><span data-stu-id="3e68d-280">dotnet tool install</span></span>](dotnet-tool-install.md) | <span data-ttu-id="3e68d-281">Instaluje narzędzie globalne na komputerze.</span><span class="sxs-lookup"><span data-stu-id="3e68d-281">Installs a Global Tool on your machine.</span></span>
[<span data-ttu-id="3e68d-282">dotnet tool list</span><span class="sxs-lookup"><span data-stu-id="3e68d-282">dotnet tool list</span></span>](dotnet-tool-list.md) | <span data-ttu-id="3e68d-283">Wyświetla listę wszystkich narzędzi globalnego aktualnie zainstalowane w domyślnym katalogu na komputerze lub w określonej ścieżce.</span><span class="sxs-lookup"><span data-stu-id="3e68d-283">Lists all Global Tools currently installed in the default directory on your machine or in the specified path.</span></span>
[<span data-ttu-id="3e68d-284">dotnet tool uninstall</span><span class="sxs-lookup"><span data-stu-id="3e68d-284">dotnet tool uninstall</span></span>](dotnet-tool-uninstall.md) | <span data-ttu-id="3e68d-285">Odinstalowuje narzędzie globalne z Twojego komputera.</span><span class="sxs-lookup"><span data-stu-id="3e68d-285">Uninstalls a Global Tool from your machine.</span></span>
[<span data-ttu-id="3e68d-286">dotnet tool update</span><span class="sxs-lookup"><span data-stu-id="3e68d-286">dotnet tool update</span></span>](dotnet-tool-update.md) | <span data-ttu-id="3e68d-287">Aktualizuje narzędzie globalne na swojej maszynie.</span><span class="sxs-lookup"><span data-stu-id="3e68d-287">Updates a Global Tool on your machine.</span></span>

### <a name="additional-tools"></a><span data-ttu-id="3e68d-288">Dodatkowe narzędzia</span><span class="sxs-lookup"><span data-stu-id="3e68d-288">Additional tools</span></span>

<span data-ttu-id="3e68d-289">Począwszy od programu .NET Core SDK 2.1.300, wiele narzędzi, które były dostępne tylko na podstawę projektu przy użyciu `DotnetCliToolReference` są teraz dostępne jako część zestawu .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="3e68d-289">Starting with .NET Core SDK 2.1.300, a number of tools that were available only on a per project basis using `DotnetCliToolReference` are now available as part of the .NET Core SDK.</span></span> <span data-ttu-id="3e68d-290">Te narzędzia są wymienione w poniższej tabeli:</span><span class="sxs-lookup"><span data-stu-id="3e68d-290">These tools are listed in the following table:</span></span>

| <span data-ttu-id="3e68d-291">Narzędzie</span><span class="sxs-lookup"><span data-stu-id="3e68d-291">Tool</span></span>                                              | <span data-ttu-id="3e68d-292">Funkcja</span><span class="sxs-lookup"><span data-stu-id="3e68d-292">Function</span></span>                                                     |
| ------------------------------------------------- | ------------------------------------------------------------ |
| <span data-ttu-id="3e68d-293">dev-certs</span><span class="sxs-lookup"><span data-stu-id="3e68d-293">dev-certs</span></span>                                         | <span data-ttu-id="3e68d-294">Tworzy i zarządza certyfikatami rozwoju.</span><span class="sxs-lookup"><span data-stu-id="3e68d-294">Creates and manages development certificates.</span></span>                |
| [<span data-ttu-id="3e68d-295">EF</span><span class="sxs-lookup"><span data-stu-id="3e68d-295">ef</span></span>](/ef/core/miscellaneous/cli/dotnet)           | <span data-ttu-id="3e68d-296">Entity Framework Core narzędzia wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="3e68d-296">Entity Framework Core command-line tools.</span></span>                    |
| <span data-ttu-id="3e68d-297">sql-cache</span><span class="sxs-lookup"><span data-stu-id="3e68d-297">sql-cache</span></span>                                         | <span data-ttu-id="3e68d-298">Narzędzia wiersza polecenia pamięci podręcznej programu SQL Server.</span><span class="sxs-lookup"><span data-stu-id="3e68d-298">SQL Server cache command-line tools.</span></span>                         |
| [<span data-ttu-id="3e68d-299">user-secrets</span><span class="sxs-lookup"><span data-stu-id="3e68d-299">user-secrets</span></span>](/aspnet/core/security/app-secrets) | <span data-ttu-id="3e68d-300">Umożliwia zarządzanie wpisami tajnymi użytkowników rozwoju.</span><span class="sxs-lookup"><span data-stu-id="3e68d-300">Manages development user secrets.</span></span>                            |
| [<span data-ttu-id="3e68d-301">watch</span><span class="sxs-lookup"><span data-stu-id="3e68d-301">watch</span></span>](/aspnet/core/tutorials/dotnet-watch)      | <span data-ttu-id="3e68d-302">Uruchamia obserwatora pliku, który uruchamia polecenie, gdy zmienią się pliki.</span><span class="sxs-lookup"><span data-stu-id="3e68d-302">Starts a file watcher that runs a command when files change.</span></span> |

<span data-ttu-id="3e68d-303">Aby uzyskać więcej informacji na temat każdego z narzędzi, wpisz `dotnet <tool-name> --help`.</span><span class="sxs-lookup"><span data-stu-id="3e68d-303">For more information about each tool, type `dotnet <tool-name> --help`.</span></span>

## <a name="examples"></a><span data-ttu-id="3e68d-304">Przykłady</span><span class="sxs-lookup"><span data-stu-id="3e68d-304">Examples</span></span>

<span data-ttu-id="3e68d-305">Tworzy nową aplikację konsoli .NET Core:</span><span class="sxs-lookup"><span data-stu-id="3e68d-305">Creates a new .NET Core console application:</span></span>

`dotnet new console`

<span data-ttu-id="3e68d-306">Przywróć zależności dla danej aplikacji:</span><span class="sxs-lookup"><span data-stu-id="3e68d-306">Restore dependencies for a given application:</span></span>

`dotnet restore`

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

<span data-ttu-id="3e68d-307">Tworzenie projektu i jego zależności w danym katalogu:</span><span class="sxs-lookup"><span data-stu-id="3e68d-307">Build a project and its dependencies in a given directory:</span></span>

`dotnet build`

<span data-ttu-id="3e68d-308">Uruchamianie aplikacji biblioteki DLL, takich jak `myapp.dll`:</span><span class="sxs-lookup"><span data-stu-id="3e68d-308">Run an application DLL, such as `myapp.dll`:</span></span>

`dotnet myapp.dll`

## <a name="environment-variables"></a><span data-ttu-id="3e68d-309">Zmienne środowiskowe</span><span class="sxs-lookup"><span data-stu-id="3e68d-309">Environment variables</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="3e68d-310">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="3e68d-310">.NET Core 2.1</span></span>](#tab/netcore21)

`DOTNET_PACKAGES`

<span data-ttu-id="3e68d-311">Pakiet główny pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="3e68d-311">The primary package cache.</span></span> <span data-ttu-id="3e68d-312">Jeśli nie został ustawiony, jego wartość domyślna to `$HOME/.nuget/packages` w systemach Unix lub `%HOME%\NuGet\Packages` na Windows.</span><span class="sxs-lookup"><span data-stu-id="3e68d-312">If not set, it defaults to `$HOME/.nuget/packages` on Unix or `%HOME%\NuGet\Packages` on Windows.</span></span>

`DOTNET_SERVICING`

<span data-ttu-id="3e68d-313">Określa lokalizację obsługi indeksu do użycia przez hosta udostępnionych podczas ładowania środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="3e68d-313">Specifies the location of the servicing index to use by the shared host when loading the runtime.</span></span>

`DOTNET_CLI_TELEMETRY_OPTOUT`

<span data-ttu-id="3e68d-314">Określa, czy dane dotyczące użycia narzędzia .NET Core jest zbierane i przesyłane do firmy Microsoft.</span><span class="sxs-lookup"><span data-stu-id="3e68d-314">Specifies whether data about the .NET Core tools usage is collected and sent to Microsoft.</span></span> <span data-ttu-id="3e68d-315">Ustaw `true` można zrezygnować z funkcji danych telemetrycznych (wartości `true`, `1`, lub `yes` zaakceptowane).</span><span class="sxs-lookup"><span data-stu-id="3e68d-315">Set to `true` to opt-out of the telemetry feature (values `true`, `1`, or `yes` accepted).</span></span> <span data-ttu-id="3e68d-316">W przeciwnym wypadku ustaw `false` można zdecydować się na funkcje telemetrii (wartości `false`, `0`, lub `no` zaakceptowane).</span><span class="sxs-lookup"><span data-stu-id="3e68d-316">Otherwise, set to `false` to opt into the telemetry features (values `false`, `0`, or `no` accepted).</span></span> <span data-ttu-id="3e68d-317">Jeśli nie jest ustawiona, wartość domyślna to `false` i funkcja telemetrii jest aktywna.</span><span class="sxs-lookup"><span data-stu-id="3e68d-317">If not set, the default is `false` and the telemetry feature is active.</span></span>

`DOTNET_MULTILEVEL_LOOKUP`

<span data-ttu-id="3e68d-318">Określa, czy środowiska uruchomieniowego, udostępnionej platformy lub zestawu SDK platformy .NET Core nie są rozwiązane z globalnej lokalizacji.</span><span class="sxs-lookup"><span data-stu-id="3e68d-318">Specifies whether .NET Core runtime, shared framework, or SDK are resolved from the global location.</span></span> <span data-ttu-id="3e68d-319">Jeśli nie został ustawiony, jego wartość domyślna to `true`.</span><span class="sxs-lookup"><span data-stu-id="3e68d-319">If not set, it defaults to `true`.</span></span> <span data-ttu-id="3e68d-320">Ustaw `false` rozwiązania z globalnej lokalizacji i izolowanych instalacji platformy .NET Core (wartości `0` lub `false` są akceptowane).</span><span class="sxs-lookup"><span data-stu-id="3e68d-320">Set to `false` to not resolve from the global location and have isolated .NET Core installations (values `0` or `false` are accepted).</span></span> <span data-ttu-id="3e68d-321">Aby uzyskać więcej informacji na temat wyszukiwania wielopoziomowe zobacz [wyszukiwania SharedFX wielopoziomowymi](https://github.com/dotnet/core-setup/blob/master/Documentation/design-docs/multilevel-sharedfx-lookup.md).</span><span class="sxs-lookup"><span data-stu-id="3e68d-321">For more information about multi-level lookup, see [Multi-level SharedFX Lookup](https://github.com/dotnet/core-setup/blob/master/Documentation/design-docs/multilevel-sharedfx-lookup.md).</span></span>

`DOTNET_ROLL_FORWARD_ON_NO_CANDIDATE_FX`

<span data-ttu-id="3e68d-322">Wyłącza wersja pomocnicza przenoszenie do przodu, jeśli ustawiono `0`.</span><span class="sxs-lookup"><span data-stu-id="3e68d-322">Disables minor version roll forward, if set to `0`.</span></span> <span data-ttu-id="3e68d-323">Aby uzyskać więcej informacji, zobacz [uaktualniane](../whats-new/dotnet-core-2-1.md#roll-forward).</span><span class="sxs-lookup"><span data-stu-id="3e68d-323">For more information, see [Roll forward](../whats-new/dotnet-core-2-1.md#roll-forward).</span></span>

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="3e68d-324">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="3e68d-324">.NET Core 2.0</span></span>](#tab/netcore20)

`DOTNET_PACKAGES`

<span data-ttu-id="3e68d-325">Pakiet główny pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="3e68d-325">The primary package cache.</span></span> <span data-ttu-id="3e68d-326">Jeśli nie został ustawiony, jego wartość domyślna to `$HOME/.nuget/packages` w systemach Unix lub `%HOME%\NuGet\Packages` na Windows.</span><span class="sxs-lookup"><span data-stu-id="3e68d-326">If not set, it defaults to `$HOME/.nuget/packages` on Unix or `%HOME%\NuGet\Packages` on Windows.</span></span>

`DOTNET_SERVICING`

<span data-ttu-id="3e68d-327">Określa lokalizację obsługi indeksu do użycia przez hosta udostępnionych podczas ładowania środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="3e68d-327">Specifies the location of the servicing index to use by the shared host when loading the runtime.</span></span>

`DOTNET_CLI_TELEMETRY_OPTOUT`

<span data-ttu-id="3e68d-328">Określa, czy dane dotyczące użycia narzędzia .NET Core jest zbierane i przesyłane do firmy Microsoft.</span><span class="sxs-lookup"><span data-stu-id="3e68d-328">Specifies whether data about the .NET Core tools usage is collected and sent to Microsoft.</span></span> <span data-ttu-id="3e68d-329">Ustaw `true` można zrezygnować z funkcji danych telemetrycznych (wartości `true`, `1`, lub `yes` zaakceptowane).</span><span class="sxs-lookup"><span data-stu-id="3e68d-329">Set to `true` to opt-out of the telemetry feature (values `true`, `1`, or `yes` accepted).</span></span> <span data-ttu-id="3e68d-330">W przeciwnym wypadku ustaw `false` można zdecydować się na funkcje telemetrii (wartości `false`, `0`, lub `no` zaakceptowane).</span><span class="sxs-lookup"><span data-stu-id="3e68d-330">Otherwise, set to `false` to opt into the telemetry features (values `false`, `0`, or `no` accepted).</span></span> <span data-ttu-id="3e68d-331">Jeśli nie jest ustawiona, wartość domyślna to `false` i funkcja telemetrii jest aktywna.</span><span class="sxs-lookup"><span data-stu-id="3e68d-331">If not set, the default is `false` and the telemetry feature is active.</span></span>

`DOTNET_MULTILEVEL_LOOKUP`

<span data-ttu-id="3e68d-332">Określa, czy środowiska uruchomieniowego, udostępnionej platformy lub zestawu SDK platformy .NET Core nie są rozwiązane z globalnej lokalizacji.</span><span class="sxs-lookup"><span data-stu-id="3e68d-332">Specifies whether .NET Core runtime, shared framework, or SDK are resolved from the global location.</span></span> <span data-ttu-id="3e68d-333">Jeśli nie został ustawiony, jego wartość domyślna to `true`.</span><span class="sxs-lookup"><span data-stu-id="3e68d-333">If not set, it defaults to `true`.</span></span> <span data-ttu-id="3e68d-334">Ustaw `false` rozwiązania z globalnej lokalizacji i izolowanych instalacji platformy .NET Core (wartości `0` lub `false` są akceptowane).</span><span class="sxs-lookup"><span data-stu-id="3e68d-334">Set to `false` to not resolve from the global location and have isolated .NET Core installations (values `0` or `false` are accepted).</span></span> <span data-ttu-id="3e68d-335">Aby uzyskać więcej informacji na temat wyszukiwania wielopoziomowe zobacz [wyszukiwania SharedFX wielopoziomowymi](https://github.com/dotnet/core-setup/blob/master/Documentation/design-docs/multilevel-sharedfx-lookup.md).</span><span class="sxs-lookup"><span data-stu-id="3e68d-335">For more information about multi-level lookup, see [Multi-level SharedFX Lookup](https://github.com/dotnet/core-setup/blob/master/Documentation/design-docs/multilevel-sharedfx-lookup.md).</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="3e68d-336">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="3e68d-336">.NET Core 1.x</span></span>](#tab/netcore1x)

`DOTNET_PACKAGES`

<span data-ttu-id="3e68d-337">Pakiet główny pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="3e68d-337">The primary package cache.</span></span> <span data-ttu-id="3e68d-338">Jeśli nie został ustawiony, jego wartość domyślna to `$HOME/.nuget/packages` w systemach Unix lub `%HOME%\NuGet\Packages` na Windows.</span><span class="sxs-lookup"><span data-stu-id="3e68d-338">If not set, it defaults to `$HOME/.nuget/packages` on Unix or `%HOME%\NuGet\Packages` on Windows.</span></span>

`DOTNET_SERVICING`

<span data-ttu-id="3e68d-339">Określa lokalizację obsługi indeksu do użycia przez hosta udostępnionych podczas ładowania środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="3e68d-339">Specifies the location of the servicing index to use by the shared host when loading the runtime.</span></span>

`DOTNET_CLI_TELEMETRY_OPTOUT`

<span data-ttu-id="3e68d-340">Określa, czy dane dotyczące użycia narzędzia .NET Core jest zbierane i przesyłane do firmy Microsoft.</span><span class="sxs-lookup"><span data-stu-id="3e68d-340">Specifies whether data about the .NET Core tools usage is collected and sent to Microsoft.</span></span> <span data-ttu-id="3e68d-341">Ustaw `true` można zrezygnować z funkcji danych telemetrycznych (wartości `true`, `1`, lub `yes` zaakceptowane).</span><span class="sxs-lookup"><span data-stu-id="3e68d-341">Set to `true` to opt-out of the telemetry feature (values `true`, `1`, or `yes` accepted).</span></span> <span data-ttu-id="3e68d-342">W przeciwnym wypadku ustaw `false` można zdecydować się na funkcje telemetrii (wartości `false`, `0`, lub `no` zaakceptowane).</span><span class="sxs-lookup"><span data-stu-id="3e68d-342">Otherwise, set to `false` to opt into the telemetry features (values `false`, `0`, or `no` accepted).</span></span> <span data-ttu-id="3e68d-343">Jeśli nie jest ustawiona, wartość domyślna to `false` i funkcja telemetrii jest aktywna.</span><span class="sxs-lookup"><span data-stu-id="3e68d-343">If not set, the default is `false` and the telemetry feature is active.</span></span>

---
