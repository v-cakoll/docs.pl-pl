---
title: polecenia DotNet — interfejs wiersza polecenia platformy .NET Core
description: Więcej informacji na temat polecenia dotnet (ogólny sterownik dla narzędzi interfejsu wiersza polecenia platformy .NET Core) i sposób jej użycia.
author: mairaw
ms.author: mairaw
ms.date: 06/04/2018
ms.openlocfilehash: 53e8f8bab1cbaabaa7926aa68197c18843b0b637
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/14/2018
ms.locfileid: "45615580"
---
# <a name="dotnet-command"></a><span data-ttu-id="10149-103">polecenia DotNet</span><span class="sxs-lookup"><span data-stu-id="10149-103">dotnet command</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="10149-104">Nazwa</span><span class="sxs-lookup"><span data-stu-id="10149-104">Name</span></span>

<span data-ttu-id="10149-105">`dotnet` — Narzędzie służące do zarządzania kodu źródłowego .NET i plikach binarnych.</span><span class="sxs-lookup"><span data-stu-id="10149-105">`dotnet` - A tool for managing .NET source code and binaries.</span></span>

## <a name="synopsis"></a><span data-ttu-id="10149-106">Streszczenie</span><span class="sxs-lookup"><span data-stu-id="10149-106">Synopsis</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="10149-107">.NET core 2.1</span><span class="sxs-lookup"><span data-stu-id="10149-107">.NET Core 2.1</span></span>](#tab/netcore21)
```
dotnet [command] [arguments] [--additional-deps] [--additionalprobingpath] [-d|--diagnostics] [--fx-version]
    [-h|--help] [--info] [--list-runtimes] [--list-sdks] [--roll-forward-on-no-candidate-fx] [-v|--verbosity] [--version]
```
# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="10149-108">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="10149-108">.NET Core 2.0</span></span>](#tab/netcore20)
```
dotnet [command] [arguments] [--additional-deps] [--additionalprobingpath] [-d|--diagnostics]
    [--fx-version] [-h|--help] [--info] [--roll-forward-on-no-candidate-fx] [-v|--verbosity] [--version]
```
# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="10149-109">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="10149-109">.NET Core 1.x</span></span>](#tab/netcore1x)
```
dotnet [command] [arguments] [--additionalprobingpath] [-d|--diagnostics] [--fx-version]
    [-h|--help] [--info] [-v|--verbosity] [--version]
```
---

## <a name="description"></a><span data-ttu-id="10149-110">Opis</span><span class="sxs-lookup"><span data-stu-id="10149-110">Description</span></span>

<span data-ttu-id="10149-111">`dotnet` to narzędzie do zarządzania kodu źródłowego .NET i pliki binarne.</span><span class="sxs-lookup"><span data-stu-id="10149-111">`dotnet` is a tool for managing .NET source code and binaries.</span></span> <span data-ttu-id="10149-112">Udostępnia ona polecenia, które wykonują określone zadania, takie jak [ `dotnet build` ](dotnet-build.md) i [ `dotnet run` ](dotnet-run.md).</span><span class="sxs-lookup"><span data-stu-id="10149-112">It exposes commands that perform specific tasks, such as [`dotnet build`](dotnet-build.md) and [`dotnet run`](dotnet-run.md).</span></span> <span data-ttu-id="10149-113">Każde polecenie definiuje swój własny argumentów.</span><span class="sxs-lookup"><span data-stu-id="10149-113">Each command defines its own arguments.</span></span> <span data-ttu-id="10149-114">Typ `--help` zatwierdzając każde z nich do dostępu krótki opis dokumentacji pomocy.</span><span class="sxs-lookup"><span data-stu-id="10149-114">Type `--help` after each command to access brief help documentation.</span></span>

<span data-ttu-id="10149-115">`dotnet` może służyć do uruchamiania aplikacji, określając aplikacji biblioteki DLL, takie jak `dotnet myapp.dll`.</span><span class="sxs-lookup"><span data-stu-id="10149-115">`dotnet` can be used to run applications, by specifying an application DLL, such as `dotnet myapp.dll`.</span></span> <span data-ttu-id="10149-116">Zobacz [wdrażanie aplikacji .NET Core](../deploying/index.md) dla Aby dowiedzieć się więcej o opcjach wdrażania.</span><span class="sxs-lookup"><span data-stu-id="10149-116">See [.NET Core application deployment](../deploying/index.md) for to learn about deployment options.</span></span>

## <a name="options"></a><span data-ttu-id="10149-117">Opcje</span><span class="sxs-lookup"><span data-stu-id="10149-117">Options</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="10149-118">.NET core 2.1</span><span class="sxs-lookup"><span data-stu-id="10149-118">.NET Core 2.1</span></span>](#tab/netcore21)

`--additional-deps <PATH>`

<span data-ttu-id="10149-119">Ścieżka do dodatkowych *deps.json* pliku.</span><span class="sxs-lookup"><span data-stu-id="10149-119">Path to additional *deps.json* file.</span></span>

`--additionalprobingpath <PATH>`

<span data-ttu-id="10149-120">Ścieżki zawierające sondowania zasad i zestawy do sondowania.</span><span class="sxs-lookup"><span data-stu-id="10149-120">Path containing probing policy and assemblies to probe.</span></span>

`-d|--diagnostics`

<span data-ttu-id="10149-121">Umożliwia diagnostyczne dane wyjściowe.</span><span class="sxs-lookup"><span data-stu-id="10149-121">Enables diagnostic output.</span></span>

`--fx-version <VERSION>`

<span data-ttu-id="10149-122">Wersja środowiska uruchomieniowego .NET Core do użycia, aby uruchomić aplikację.</span><span class="sxs-lookup"><span data-stu-id="10149-122">Version of the .NET Core runtime to use to run the application.</span></span>

`-h|--help`

<span data-ttu-id="10149-123">Wyświetla dokumentację dotyczącą danego polecenia, takie jak `dotnet build --help`.</span><span class="sxs-lookup"><span data-stu-id="10149-123">Prints out documentation for a given command, such as `dotnet build --help`.</span></span> <span data-ttu-id="10149-124">`dotnet --help` Wyświetla listę dostępnych poleceń.</span><span class="sxs-lookup"><span data-stu-id="10149-124">`dotnet --help` prints a list of available commands.</span></span>

`--info`

<span data-ttu-id="10149-125">Drukuje szczegółowe informacje dotyczące instalacji platformy .NET Core i środowiska maszyny, takich jak bieżący system operacyjny i zatwierdzenie SHA wersji platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="10149-125">Prints out detailed information about a .NET Core installation and the machine environment, such as the current operating system, and commit SHA of the .NET Core version.</span></span>

`--list-runtimes`

<span data-ttu-id="10149-126">Wyświetla zainstalowane środowiska uruchomieniowe platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="10149-126">Displays the installed .NET Core runtimes.</span></span>

`--list-sdks`

<span data-ttu-id="10149-127">Wyświetla zainstalowanych zestawów .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="10149-127">Displays the installed .NET Core SDKs.</span></span>

`--roll-forward-on-no-candidate-fx`

 <span data-ttu-id="10149-128">Wyłącza wersja pomocnicza przenoszenie do przodu, jeśli ustawiono `0`.</span><span class="sxs-lookup"><span data-stu-id="10149-128">Disables minor version roll forward, if set to `0`.</span></span> <span data-ttu-id="10149-129">Aby uzyskać więcej informacji, zobacz [uaktualniane](../whats-new/dotnet-core-2-1.md#roll-forward).</span><span class="sxs-lookup"><span data-stu-id="10149-129">For more information, see [Roll forward](../whats-new/dotnet-core-2-1.md#roll-forward).</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="10149-130">Ustawia poziom szczegółowości polecenia.</span><span class="sxs-lookup"><span data-stu-id="10149-130">Sets the verbosity level of the command.</span></span> <span data-ttu-id="10149-131">Dozwolone wartości to `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, i `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="10149-131">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="10149-132">Nie jest obsługiwana w każdym poleceniu; zobacz stronę określone polecenie, aby określić, jeśli ta opcja jest dostępna.</span><span class="sxs-lookup"><span data-stu-id="10149-132">Not supported in every command; see specific command page to determine if this option is available.</span></span>

`--version`

<span data-ttu-id="10149-133">Drukuje wersję zestawu .NET Core SDK w użyciu.</span><span class="sxs-lookup"><span data-stu-id="10149-133">Prints out the version of the .NET Core SDK in use.</span></span>

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="10149-134">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="10149-134">.NET Core 2.0</span></span>](#tab/netcore20)

`--additional-deps <PATH>`

<span data-ttu-id="10149-135">Ścieżka do dodatkowych *deps.json* pliku.</span><span class="sxs-lookup"><span data-stu-id="10149-135">Path to additional *deps.json* file.</span></span>

`--additionalprobingpath <PATH>`

<span data-ttu-id="10149-136">Ścieżki zawierające sondowania zasad i zestawy do sondowania.</span><span class="sxs-lookup"><span data-stu-id="10149-136">Path containing probing policy and assemblies to probe.</span></span>

`-d|--diagnostics`

<span data-ttu-id="10149-137">Umożliwia diagnostyczne dane wyjściowe.</span><span class="sxs-lookup"><span data-stu-id="10149-137">Enables diagnostic output.</span></span>

`--fx-version <VERSION>`

<span data-ttu-id="10149-138">Wersja środowiska uruchomieniowego .NET Core do użycia, aby uruchomić aplikację.</span><span class="sxs-lookup"><span data-stu-id="10149-138">Version of the .NET Core runtime to use to run the application.</span></span>

`-h|--help`

<span data-ttu-id="10149-139">Wyświetla dokumentację dotyczącą danego polecenia, takie jak `dotnet build --help`.</span><span class="sxs-lookup"><span data-stu-id="10149-139">Prints out documentation for a given command, such as `dotnet build --help`.</span></span> <span data-ttu-id="10149-140">`dotnet --help` Wyświetla listę dostępnych poleceń.</span><span class="sxs-lookup"><span data-stu-id="10149-140">`dotnet --help` prints a list of available commands.</span></span>

`--info`

<span data-ttu-id="10149-141">Drukuje szczegółowe informacje dotyczące instalacji platformy .NET Core i środowiska maszyny, takich jak bieżący system operacyjny i zatwierdzenie SHA wersji platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="10149-141">Prints out detailed information about a .NET Core installation and the machine environment, such as the current operating system, and commit SHA of the .NET Core version.</span></span>

`--roll-forward-on-no-candidate-fx`

 <span data-ttu-id="10149-142">Wyłącza wersja pomocnicza przenoszenie do przodu, jeśli ustawiono `0`.</span><span class="sxs-lookup"><span data-stu-id="10149-142">Disables minor version roll forward, if set to `0`.</span></span> <span data-ttu-id="10149-143">Aby uzyskać więcej informacji, zobacz [uaktualniane](../whats-new/dotnet-core-2-1.md#roll-forward).</span><span class="sxs-lookup"><span data-stu-id="10149-143">For more information, see [Roll forward](../whats-new/dotnet-core-2-1.md#roll-forward).</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="10149-144">Ustawia poziom szczegółowości polecenia.</span><span class="sxs-lookup"><span data-stu-id="10149-144">Sets the verbosity level of the command.</span></span> <span data-ttu-id="10149-145">Dozwolone wartości to `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, i `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="10149-145">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="10149-146">Nie jest obsługiwana w każdym poleceniu; zobacz stronę określone polecenie, aby określić, jeśli ta opcja jest dostępna.</span><span class="sxs-lookup"><span data-stu-id="10149-146">Not supported in every command; see specific command page to determine if this option is available.</span></span>

`--version`

<span data-ttu-id="10149-147">Drukuje wersję zestawu .NET Core SDK w użyciu.</span><span class="sxs-lookup"><span data-stu-id="10149-147">Prints out the version of the .NET Core SDK in use.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="10149-148">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="10149-148">.NET Core 1.x</span></span>](#tab/netcore1x)

`--additionalprobingpath <PATH>`

<span data-ttu-id="10149-149">Ścieżki zawierające sondowania zasad i zestawy do sondowania.</span><span class="sxs-lookup"><span data-stu-id="10149-149">Path containing probing policy and assemblies to probe.</span></span>

`-d|--diagnostics`

<span data-ttu-id="10149-150">Umożliwia diagnostyczne dane wyjściowe.</span><span class="sxs-lookup"><span data-stu-id="10149-150">Enables diagnostic output.</span></span>

`--fx-version <VERSION>`

<span data-ttu-id="10149-151">Wersja środowiska uruchomieniowego .NET Core do użycia, aby uruchomić aplikację.</span><span class="sxs-lookup"><span data-stu-id="10149-151">Version of the .NET Core runtime to use to run the application.</span></span>

`-h|--help`

<span data-ttu-id="10149-152">Wyświetla dokumentację dotyczącą danego polecenia, takie jak `dotnet build --help`.</span><span class="sxs-lookup"><span data-stu-id="10149-152">Prints out documentation for a given command, such as `dotnet build --help`.</span></span> <span data-ttu-id="10149-153">`dotnet --help` Wyświetla listę dostępnych poleceń.</span><span class="sxs-lookup"><span data-stu-id="10149-153">`dotnet --help` prints a list of available commands.</span></span>

`--info`

<span data-ttu-id="10149-154">Drukuje szczegółowe informacje dotyczące instalacji platformy .NET Core i środowiska maszyny, takich jak bieżący system operacyjny i zatwierdzenie SHA wersji platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="10149-154">Prints out detailed information about a .NET Core installation and the machine environment, such as the current operating system, and commit SHA of the .NET Core version.</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="10149-155">Ustawia poziom szczegółowości polecenia.</span><span class="sxs-lookup"><span data-stu-id="10149-155">Sets the verbosity level of the command.</span></span> <span data-ttu-id="10149-156">Dozwolone wartości to `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, i `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="10149-156">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="10149-157">Nie jest obsługiwana w każdym poleceniu; zobacz stronę określone polecenie, aby określić, jeśli ta opcja jest dostępna.</span><span class="sxs-lookup"><span data-stu-id="10149-157">Not supported in every command; see specific command page to determine if this option is available.</span></span>

`--version`

<span data-ttu-id="10149-158">Drukuje wersję zestawu .NET Core SDK w użyciu.</span><span class="sxs-lookup"><span data-stu-id="10149-158">Prints out the version of the .NET Core SDK in use.</span></span>

---

## <a name="dotnet-commands"></a><span data-ttu-id="10149-159">polecenia DotNet</span><span class="sxs-lookup"><span data-stu-id="10149-159">dotnet commands</span></span>

### <a name="general"></a><span data-ttu-id="10149-160">Ogólne</span><span class="sxs-lookup"><span data-stu-id="10149-160">General</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="10149-161">.NET core 2.1</span><span class="sxs-lookup"><span data-stu-id="10149-161">.NET Core 2.1</span></span>](#tab/netcore21)

| <span data-ttu-id="10149-162">Polecenie</span><span class="sxs-lookup"><span data-stu-id="10149-162">Command</span></span>                                       | <span data-ttu-id="10149-163">Funkcja</span><span class="sxs-lookup"><span data-stu-id="10149-163">Function</span></span>                                                            |
| --------------------------------------------- | ------------------------------------------------------------------- |
| [<span data-ttu-id="10149-164">dotnet build</span><span class="sxs-lookup"><span data-stu-id="10149-164">dotnet build</span></span>](dotnet-build.md)               | <span data-ttu-id="10149-165">Tworzy aplikację .NET Core.</span><span class="sxs-lookup"><span data-stu-id="10149-165">Builds a .NET Core application.</span></span>                                     |
| [<span data-ttu-id="10149-166">dotnet build-server</span><span class="sxs-lookup"><span data-stu-id="10149-166">dotnet build-server</span></span>](dotnet-build-server.md) | <span data-ttu-id="10149-167">Wchodzi w interakcję z serwerami, uruchomione przez kompilację.</span><span class="sxs-lookup"><span data-stu-id="10149-167">Interacts with servers started by a build.</span></span>                          |
| [<span data-ttu-id="10149-168">dotnet clean</span><span class="sxs-lookup"><span data-stu-id="10149-168">dotnet clean</span></span>](dotnet-clean.md)               | <span data-ttu-id="10149-169">Czysta kompilacja danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="10149-169">Clean build outputs.</span></span>                                                |
| [<span data-ttu-id="10149-170">dotnet help</span><span class="sxs-lookup"><span data-stu-id="10149-170">dotnet help</span></span>](dotnet-help.md)                 | <span data-ttu-id="10149-171">Zawiera bardziej szczegółowe dokumentację online dla polecenia.</span><span class="sxs-lookup"><span data-stu-id="10149-171">Shows more detailed documentation online for the command.</span></span>           |
| [<span data-ttu-id="10149-172">dotnet migrate</span><span class="sxs-lookup"><span data-stu-id="10149-172">dotnet migrate</span></span>](dotnet-migrate.md)           | <span data-ttu-id="10149-173">Prawidłowy projekt w wersji 2 jest migrowana do projektu .NET Core SDK 1.0.</span><span class="sxs-lookup"><span data-stu-id="10149-173">Migrates a valid Preview 2 project to a .NET Core SDK 1.0 project.</span></span>  |
| [<span data-ttu-id="10149-174">dotnet msbuild</span><span class="sxs-lookup"><span data-stu-id="10149-174">dotnet msbuild</span></span>](dotnet-msbuild.md)           | <span data-ttu-id="10149-175">Zapewnia dostęp do wiersza polecenia programu MSBuild.</span><span class="sxs-lookup"><span data-stu-id="10149-175">Provides access to the MSBuild command line.</span></span>                        |
| [<span data-ttu-id="10149-176">dotnet new</span><span class="sxs-lookup"><span data-stu-id="10149-176">dotnet new</span></span>](dotnet-new.md)                   | <span data-ttu-id="10149-177">Inicjuje projekt C# lub F # dla danego szablonu.</span><span class="sxs-lookup"><span data-stu-id="10149-177">Initializes a C# or F# project for a given template.</span></span>                |
| [<span data-ttu-id="10149-178">dotnet pack</span><span class="sxs-lookup"><span data-stu-id="10149-178">dotnet pack</span></span>](dotnet-pack.md)                 | <span data-ttu-id="10149-179">Tworzy pakiet NuGet kodu.</span><span class="sxs-lookup"><span data-stu-id="10149-179">Creates a NuGet package of your code.</span></span>                               |
| [<span data-ttu-id="10149-180">dotnet publish</span><span class="sxs-lookup"><span data-stu-id="10149-180">dotnet publish</span></span>](dotnet-publish.md)           | <span data-ttu-id="10149-181">Publikuje aplikacji autonomicznej .NET framework-zależnych od ustawień lokalnych lub niezależna.</span><span class="sxs-lookup"><span data-stu-id="10149-181">Publishes a .NET framework-dependent or self-contained application.</span></span> |
| [<span data-ttu-id="10149-182">dotnet restore</span><span class="sxs-lookup"><span data-stu-id="10149-182">dotnet restore</span></span>](dotnet-restore.md)           | <span data-ttu-id="10149-183">Przywraca zależności dla danej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="10149-183">Restores the dependencies for a given application.</span></span>                  |
| [<span data-ttu-id="10149-184">dotnet run</span><span class="sxs-lookup"><span data-stu-id="10149-184">dotnet run</span></span>](dotnet-run.md)                   | <span data-ttu-id="10149-185">Ze źródła do uruchamiania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="10149-185">Runs the application from source.</span></span>                                   |
| [<span data-ttu-id="10149-186">dotnet sln</span><span class="sxs-lookup"><span data-stu-id="10149-186">dotnet sln</span></span>](dotnet-sln.md)                   | <span data-ttu-id="10149-187">Opcje służące do dodawania, usuwania i wyświetlić listę projektów w pliku rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="10149-187">Options to add, remove, and list projects in a solution file.</span></span>       |
| [<span data-ttu-id="10149-188">dotnet store</span><span class="sxs-lookup"><span data-stu-id="10149-188">dotnet store</span></span>](dotnet-store.md)               | <span data-ttu-id="10149-189">Przechowuje zestawy w Magazyn pakietu środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="10149-189">Stores assemblies in the runtime package store.</span></span>                     |
| [<span data-ttu-id="10149-190">dotnet test</span><span class="sxs-lookup"><span data-stu-id="10149-190">dotnet test</span></span>](dotnet-test.md)                 | <span data-ttu-id="10149-191">Uruchamia testy za pomocą narzędzia test runner.</span><span class="sxs-lookup"><span data-stu-id="10149-191">Runs tests using a test runner.</span></span>                                     |

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="10149-192">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="10149-192">.NET Core 2.0</span></span>](#tab/netcore20)

| <span data-ttu-id="10149-193">Polecenie</span><span class="sxs-lookup"><span data-stu-id="10149-193">Command</span></span>                             | <span data-ttu-id="10149-194">Funkcja</span><span class="sxs-lookup"><span data-stu-id="10149-194">Function</span></span>                                                            |
| ----------------------------------- | ------------------------------------------------------------------- |
| [<span data-ttu-id="10149-195">dotnet build</span><span class="sxs-lookup"><span data-stu-id="10149-195">dotnet build</span></span>](dotnet-build.md)     | <span data-ttu-id="10149-196">Tworzy aplikację .NET Core.</span><span class="sxs-lookup"><span data-stu-id="10149-196">Builds a .NET Core application.</span></span>                                     |
| [<span data-ttu-id="10149-197">dotnet clean</span><span class="sxs-lookup"><span data-stu-id="10149-197">dotnet clean</span></span>](dotnet-clean.md)     | <span data-ttu-id="10149-198">Czysta kompilacja danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="10149-198">Clean build outputs.</span></span>                                              |
| [<span data-ttu-id="10149-199">dotnet help</span><span class="sxs-lookup"><span data-stu-id="10149-199">dotnet help</span></span>](dotnet-help.md)       | <span data-ttu-id="10149-200">Zawiera bardziej szczegółowe dokumentację online dla polecenia.</span><span class="sxs-lookup"><span data-stu-id="10149-200">Shows more detailed documentation online for the command.</span></span>           |
| [<span data-ttu-id="10149-201">dotnet migrate</span><span class="sxs-lookup"><span data-stu-id="10149-201">dotnet migrate</span></span>](dotnet-migrate.md) | <span data-ttu-id="10149-202">Prawidłowy projekt w wersji 2 jest migrowana do projektu .NET Core SDK 1.0.</span><span class="sxs-lookup"><span data-stu-id="10149-202">Migrates a valid Preview 2 project to a .NET Core SDK 1.0 project.</span></span>  |
| [<span data-ttu-id="10149-203">dotnet msbuild</span><span class="sxs-lookup"><span data-stu-id="10149-203">dotnet msbuild</span></span>](dotnet-msbuild.md) | <span data-ttu-id="10149-204">Zapewnia dostęp do wiersza polecenia programu MSBuild.</span><span class="sxs-lookup"><span data-stu-id="10149-204">Provides access to the MSBuild command line.</span></span>                        |
| [<span data-ttu-id="10149-205">dotnet new</span><span class="sxs-lookup"><span data-stu-id="10149-205">dotnet new</span></span>](dotnet-new.md)         | <span data-ttu-id="10149-206">Inicjuje projekt C# lub F # dla danego szablonu.</span><span class="sxs-lookup"><span data-stu-id="10149-206">Initializes a C# or F# project for a given template.</span></span>                |
| [<span data-ttu-id="10149-207">dotnet pack</span><span class="sxs-lookup"><span data-stu-id="10149-207">dotnet pack</span></span>](dotnet-pack.md)       | <span data-ttu-id="10149-208">Tworzy pakiet NuGet kodu.</span><span class="sxs-lookup"><span data-stu-id="10149-208">Creates a NuGet package of your code.</span></span>                               |
| [<span data-ttu-id="10149-209">dotnet publish</span><span class="sxs-lookup"><span data-stu-id="10149-209">dotnet publish</span></span>](dotnet-publish.md) | <span data-ttu-id="10149-210">Publikuje aplikacji autonomicznej .NET framework-zależnych od ustawień lokalnych lub niezależna.</span><span class="sxs-lookup"><span data-stu-id="10149-210">Publishes a .NET framework-dependent or self-contained application.</span></span> |
| [<span data-ttu-id="10149-211">dotnet restore</span><span class="sxs-lookup"><span data-stu-id="10149-211">dotnet restore</span></span>](dotnet-restore.md) | <span data-ttu-id="10149-212">Przywraca zależności dla danej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="10149-212">Restores the dependencies for a given application.</span></span>                  |
| [<span data-ttu-id="10149-213">dotnet run</span><span class="sxs-lookup"><span data-stu-id="10149-213">dotnet run</span></span>](dotnet-run.md)         | <span data-ttu-id="10149-214">Ze źródła do uruchamiania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="10149-214">Runs the application from source.</span></span>                                   |
| [<span data-ttu-id="10149-215">dotnet sln</span><span class="sxs-lookup"><span data-stu-id="10149-215">dotnet sln</span></span>](dotnet-sln.md)         | <span data-ttu-id="10149-216">Opcje służące do dodawania, usuwania i wyświetlić listę projektów w pliku rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="10149-216">Options to add, remove, and list projects in a solution file.</span></span>       |
| [<span data-ttu-id="10149-217">dotnet store</span><span class="sxs-lookup"><span data-stu-id="10149-217">dotnet store</span></span>](dotnet-store.md)     | <span data-ttu-id="10149-218">Przechowuje zestawy w Magazyn pakietu środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="10149-218">Stores assemblies in the runtime package store.</span></span>                     |
| [<span data-ttu-id="10149-219">dotnet test</span><span class="sxs-lookup"><span data-stu-id="10149-219">dotnet test</span></span>](dotnet-test.md)       | <span data-ttu-id="10149-220">Uruchamia testy za pomocą narzędzia test runner.</span><span class="sxs-lookup"><span data-stu-id="10149-220">Runs tests using a test runner.</span></span>                                     |

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="10149-221">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="10149-221">.NET Core 1.x</span></span>](#tab/netcore1x)

| <span data-ttu-id="10149-222">Polecenie</span><span class="sxs-lookup"><span data-stu-id="10149-222">Command</span></span>                             | <span data-ttu-id="10149-223">Funkcja</span><span class="sxs-lookup"><span data-stu-id="10149-223">Function</span></span>                                                            |
| ----------------------------------- | ------------------------------------------------------------------- |
| [<span data-ttu-id="10149-224">dotnet build</span><span class="sxs-lookup"><span data-stu-id="10149-224">dotnet build</span></span>](dotnet-build.md)     | <span data-ttu-id="10149-225">Tworzy aplikację .NET Core.</span><span class="sxs-lookup"><span data-stu-id="10149-225">Builds a .NET Core application.</span></span>                                     |
| [<span data-ttu-id="10149-226">dotnet clean</span><span class="sxs-lookup"><span data-stu-id="10149-226">dotnet clean</span></span>](dotnet-clean.md)     | <span data-ttu-id="10149-227">Czysta kompilacja danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="10149-227">Clean build outputs.</span></span>                                              |
| [<span data-ttu-id="10149-228">dotnet migrate</span><span class="sxs-lookup"><span data-stu-id="10149-228">dotnet migrate</span></span>](dotnet-migrate.md) | <span data-ttu-id="10149-229">Prawidłowy projekt w wersji 2 jest migrowana do projektu .NET Core SDK 1.0.</span><span class="sxs-lookup"><span data-stu-id="10149-229">Migrates a valid Preview 2 project to a .NET Core SDK 1.0 project.</span></span>  |
| [<span data-ttu-id="10149-230">dotnet msbuild</span><span class="sxs-lookup"><span data-stu-id="10149-230">dotnet msbuild</span></span>](dotnet-msbuild.md) | <span data-ttu-id="10149-231">Zapewnia dostęp do wiersza polecenia programu MSBuild.</span><span class="sxs-lookup"><span data-stu-id="10149-231">Provides access to the MSBuild command line.</span></span>                        |
| [<span data-ttu-id="10149-232">dotnet new</span><span class="sxs-lookup"><span data-stu-id="10149-232">dotnet new</span></span>](dotnet-new.md)         | <span data-ttu-id="10149-233">Inicjuje projekt C# lub F # dla danego szablonu.</span><span class="sxs-lookup"><span data-stu-id="10149-233">Initializes a C# or F# project for a given template.</span></span>                |
| [<span data-ttu-id="10149-234">dotnet pack</span><span class="sxs-lookup"><span data-stu-id="10149-234">dotnet pack</span></span>](dotnet-pack.md)       | <span data-ttu-id="10149-235">Tworzy pakiet NuGet kodu.</span><span class="sxs-lookup"><span data-stu-id="10149-235">Creates a NuGet package of your code.</span></span>                               |
| [<span data-ttu-id="10149-236">dotnet publish</span><span class="sxs-lookup"><span data-stu-id="10149-236">dotnet publish</span></span>](dotnet-publish.md) | <span data-ttu-id="10149-237">Publikuje aplikacji autonomicznej .NET framework-zależnych od ustawień lokalnych lub niezależna.</span><span class="sxs-lookup"><span data-stu-id="10149-237">Publishes a .NET framework-dependent or self-contained application.</span></span> |
| [<span data-ttu-id="10149-238">dotnet restore</span><span class="sxs-lookup"><span data-stu-id="10149-238">dotnet restore</span></span>](dotnet-restore.md) | <span data-ttu-id="10149-239">Przywraca zależności dla danej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="10149-239">Restores the dependencies for a given application.</span></span>                  |
| [<span data-ttu-id="10149-240">dotnet run</span><span class="sxs-lookup"><span data-stu-id="10149-240">dotnet run</span></span>](dotnet-run.md)         | <span data-ttu-id="10149-241">Ze źródła do uruchamiania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="10149-241">Runs the application from source.</span></span>                                   |
| [<span data-ttu-id="10149-242">dotnet sln</span><span class="sxs-lookup"><span data-stu-id="10149-242">dotnet sln</span></span>](dotnet-sln.md)         | <span data-ttu-id="10149-243">Opcje służące do dodawania, usuwania i wyświetlić listę projektów w pliku rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="10149-243">Options to add, remove, and list projects in a solution file.</span></span>       |
| [<span data-ttu-id="10149-244">dotnet test</span><span class="sxs-lookup"><span data-stu-id="10149-244">dotnet test</span></span>](dotnet-test.md)       | <span data-ttu-id="10149-245">Uruchamia testy za pomocą narzędzia test runner.</span><span class="sxs-lookup"><span data-stu-id="10149-245">Runs tests using a test runner.</span></span>                                     |

---

### <a name="project-references"></a><span data-ttu-id="10149-246">Odwołania do projektu</span><span class="sxs-lookup"><span data-stu-id="10149-246">Project references</span></span>

<span data-ttu-id="10149-247">Polecenie</span><span class="sxs-lookup"><span data-stu-id="10149-247">Command</span></span> | <span data-ttu-id="10149-248">Funkcja</span><span class="sxs-lookup"><span data-stu-id="10149-248">Function</span></span>
--- | ---
[<span data-ttu-id="10149-249">dotnet add reference</span><span class="sxs-lookup"><span data-stu-id="10149-249">dotnet add reference</span></span>](dotnet-add-reference.md) | <span data-ttu-id="10149-250">Dodaje odwołanie do projektu.</span><span class="sxs-lookup"><span data-stu-id="10149-250">Adds a project reference.</span></span>
[<span data-ttu-id="10149-251">dotnet list reference</span><span class="sxs-lookup"><span data-stu-id="10149-251">dotnet list reference</span></span>](dotnet-list-reference.md) | <span data-ttu-id="10149-252">Wyświetla listę odwołań do projektu.</span><span class="sxs-lookup"><span data-stu-id="10149-252">Lists project references.</span></span>
[<span data-ttu-id="10149-253">dotnet remove reference</span><span class="sxs-lookup"><span data-stu-id="10149-253">dotnet remove reference</span></span>](dotnet-remove-reference.md) | <span data-ttu-id="10149-254">Usuwa odwołanie do projektu.</span><span class="sxs-lookup"><span data-stu-id="10149-254">Removes a project reference.</span></span>

### <a name="nuget-packages"></a><span data-ttu-id="10149-255">Pakiety NuGet</span><span class="sxs-lookup"><span data-stu-id="10149-255">NuGet packages</span></span>

<span data-ttu-id="10149-256">Polecenie</span><span class="sxs-lookup"><span data-stu-id="10149-256">Command</span></span> | <span data-ttu-id="10149-257">Funkcja</span><span class="sxs-lookup"><span data-stu-id="10149-257">Function</span></span>
--- | ---
[<span data-ttu-id="10149-258">dotnet add package</span><span class="sxs-lookup"><span data-stu-id="10149-258">dotnet add package</span></span>](dotnet-add-package.md) | <span data-ttu-id="10149-259">Dodaje pakiet NuGet.</span><span class="sxs-lookup"><span data-stu-id="10149-259">Adds a NuGet package.</span></span>
[<span data-ttu-id="10149-260">dotnet remove package</span><span class="sxs-lookup"><span data-stu-id="10149-260">dotnet remove package</span></span>](dotnet-remove-package.md) | <span data-ttu-id="10149-261">Usuwa pakiet NuGet.</span><span class="sxs-lookup"><span data-stu-id="10149-261">Removes a NuGet package.</span></span>

### <a name="nuget-commands"></a><span data-ttu-id="10149-262">Polecenia NuGet</span><span class="sxs-lookup"><span data-stu-id="10149-262">NuGet commands</span></span>

<span data-ttu-id="10149-263">Polecenie</span><span class="sxs-lookup"><span data-stu-id="10149-263">Command</span></span> | <span data-ttu-id="10149-264">Funkcja</span><span class="sxs-lookup"><span data-stu-id="10149-264">Function</span></span>
--- | ---
[<span data-ttu-id="10149-265">dotnet nuget delete</span><span class="sxs-lookup"><span data-stu-id="10149-265">dotnet nuget delete</span></span>](dotnet-nuget-delete.md) | <span data-ttu-id="10149-266">Usuwa lub unlists pakietu z serwera.</span><span class="sxs-lookup"><span data-stu-id="10149-266">Deletes or unlists a package from the server.</span></span>
[<span data-ttu-id="10149-267">dotnet nuget locals</span><span class="sxs-lookup"><span data-stu-id="10149-267">dotnet nuget locals</span></span>](dotnet-nuget-locals.md) | <span data-ttu-id="10149-268">Usuwa lub wyświetla ich listę zasobów lokalnych NuGet, takie jak pamięć podręczna żądań http, tymczasowej pamięci podręcznej lub folder komputera globalnymi pakietami.</span><span class="sxs-lookup"><span data-stu-id="10149-268">Clears or lists local NuGet resources such as http-request cache, temporary cache, or machine-wide global packages folder.</span></span>
[<span data-ttu-id="10149-269">dotnet nuget push</span><span class="sxs-lookup"><span data-stu-id="10149-269">dotnet nuget push</span></span>](dotnet-nuget-push.md) | <span data-ttu-id="10149-270">Wypychanie pakietu do serwera i publikuje go.</span><span class="sxs-lookup"><span data-stu-id="10149-270">Pushes a package to the server and publishes it.</span></span>

### <a name="global-tools-commands"></a><span data-ttu-id="10149-271">Polecenia narzędzia globalne</span><span class="sxs-lookup"><span data-stu-id="10149-271">Global Tools commands</span></span>

<span data-ttu-id="10149-272">[Narzędzia programu .NET core globalnego](global-tools.md) są dostępne, począwszy od programu .NET Core SDK 2.1.300:</span><span class="sxs-lookup"><span data-stu-id="10149-272">[.NET Core Global Tools](global-tools.md) are available starting with .NET Core SDK 2.1.300:</span></span>

<span data-ttu-id="10149-273">Polecenie</span><span class="sxs-lookup"><span data-stu-id="10149-273">Command</span></span> | <span data-ttu-id="10149-274">Funkcja</span><span class="sxs-lookup"><span data-stu-id="10149-274">Function</span></span>
--- | ---
[<span data-ttu-id="10149-275">dotnet tool install</span><span class="sxs-lookup"><span data-stu-id="10149-275">dotnet tool install</span></span>](dotnet-tool-install.md) | <span data-ttu-id="10149-276">Instaluje narzędzie globalne na komputerze.</span><span class="sxs-lookup"><span data-stu-id="10149-276">Installs a Global Tool on your machine.</span></span>
[<span data-ttu-id="10149-277">dotnet tool list</span><span class="sxs-lookup"><span data-stu-id="10149-277">dotnet tool list</span></span>](dotnet-tool-list.md) | <span data-ttu-id="10149-278">Wyświetla listę wszystkich narzędzi globalnego aktualnie zainstalowane w domyślnym katalogu na komputerze lub w określonej ścieżce.</span><span class="sxs-lookup"><span data-stu-id="10149-278">Lists all Global Tools currently installed in the default directory on your machine or in the specified path.</span></span>
[<span data-ttu-id="10149-279">dotnet tool uninstall</span><span class="sxs-lookup"><span data-stu-id="10149-279">dotnet tool uninstall</span></span>](dotnet-tool-uninstall.md) | <span data-ttu-id="10149-280">Odinstalowuje narzędzie globalne z Twojego komputera.</span><span class="sxs-lookup"><span data-stu-id="10149-280">Uninstalls a Global Tool from your machine.</span></span>
[<span data-ttu-id="10149-281">dotnet tool update</span><span class="sxs-lookup"><span data-stu-id="10149-281">dotnet tool update</span></span>](dotnet-tool-update.md) | <span data-ttu-id="10149-282">Aktualizuje narzędzie globalne na swojej maszynie.</span><span class="sxs-lookup"><span data-stu-id="10149-282">Updates a Global Tool on your machine.</span></span>

### <a name="additional-tools"></a><span data-ttu-id="10149-283">Dodatkowe narzędzia</span><span class="sxs-lookup"><span data-stu-id="10149-283">Additional tools</span></span>

<span data-ttu-id="10149-284">Począwszy od programu .NET Core SDK 2.1.300, wiele narzędzi, które były dostępne tylko na podstawę projektu przy użyciu `DotnetCliToolReference` są teraz dostępne jako część zestawu .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="10149-284">Starting with .NET Core SDK 2.1.300, a number of tools that were available only on a per project basis using `DotnetCliToolReference` are now available as part of the .NET Core SDK.</span></span> <span data-ttu-id="10149-285">Te narzędzia są wymienione w poniższej tabeli:</span><span class="sxs-lookup"><span data-stu-id="10149-285">These tools are listed in the following table:</span></span>

| <span data-ttu-id="10149-286">Narzędzie</span><span class="sxs-lookup"><span data-stu-id="10149-286">Tool</span></span>                                              | <span data-ttu-id="10149-287">Funkcja</span><span class="sxs-lookup"><span data-stu-id="10149-287">Function</span></span>                                                     |
| ------------------------------------------------- | ------------------------------------------------------------ |
| <span data-ttu-id="10149-288">dev-certs</span><span class="sxs-lookup"><span data-stu-id="10149-288">dev-certs</span></span>                                         | <span data-ttu-id="10149-289">Tworzy i zarządza certyfikatami rozwoju.</span><span class="sxs-lookup"><span data-stu-id="10149-289">Creates and manages development certificates.</span></span>                |
| [<span data-ttu-id="10149-290">EF</span><span class="sxs-lookup"><span data-stu-id="10149-290">ef</span></span>](/ef/core/miscellaneous/cli/dotnet)           | <span data-ttu-id="10149-291">Entity Framework Core narzędzia wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="10149-291">Entity Framework Core command-line tools.</span></span>                    |
| <span data-ttu-id="10149-292">pamięć podręczna SQL</span><span class="sxs-lookup"><span data-stu-id="10149-292">sql-cache</span></span>                                         | <span data-ttu-id="10149-293">Narzędzia wiersza polecenia pamięci podręcznej programu SQL Server.</span><span class="sxs-lookup"><span data-stu-id="10149-293">SQL Server cache command-line tools.</span></span>                         |
| [<span data-ttu-id="10149-294">wpisami tajnymi użytkowników</span><span class="sxs-lookup"><span data-stu-id="10149-294">user-secrets</span></span>](/aspnet/core/security/app-secrets) | <span data-ttu-id="10149-295">Umożliwia zarządzanie wpisami tajnymi użytkowników rozwoju.</span><span class="sxs-lookup"><span data-stu-id="10149-295">Manages development user secrets.</span></span>                            |
| [<span data-ttu-id="10149-296">Wyrażenie kontrolne</span><span class="sxs-lookup"><span data-stu-id="10149-296">watch</span></span>](/aspnet/core/tutorials/dotnet-watch)      | <span data-ttu-id="10149-297">Uruchamia obserwatora pliku, który uruchamia polecenie, gdy zmienią się pliki.</span><span class="sxs-lookup"><span data-stu-id="10149-297">Starts a file watcher that runs a command when files change.</span></span> |

<span data-ttu-id="10149-298">Aby uzyskać więcej informacji na temat każdego z narzędzi, wpisz `dotnet <tool-name> --help`.</span><span class="sxs-lookup"><span data-stu-id="10149-298">For more information about each tool, type `dotnet <tool-name> --help`.</span></span>

## <a name="examples"></a><span data-ttu-id="10149-299">Przykłady</span><span class="sxs-lookup"><span data-stu-id="10149-299">Examples</span></span>

<span data-ttu-id="10149-300">Tworzy nową aplikację konsoli .NET Core:</span><span class="sxs-lookup"><span data-stu-id="10149-300">Creates a new .NET Core console application:</span></span>

`dotnet new console`

<span data-ttu-id="10149-301">Przywróć zależności dla danej aplikacji:</span><span class="sxs-lookup"><span data-stu-id="10149-301">Restore dependencies for a given application:</span></span>

`dotnet restore`

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

<span data-ttu-id="10149-302">Tworzenie projektu i jego zależności w danym katalogu:</span><span class="sxs-lookup"><span data-stu-id="10149-302">Build a project and its dependencies in a given directory:</span></span>

`dotnet build`

<span data-ttu-id="10149-303">Uruchamianie aplikacji biblioteki DLL, takich jak `myapp.dll`:</span><span class="sxs-lookup"><span data-stu-id="10149-303">Run an application DLL, such as `myapp.dll`:</span></span>

`dotnet myapp.dll`

## <a name="environment-variables"></a><span data-ttu-id="10149-304">Zmienne środowiskowe</span><span class="sxs-lookup"><span data-stu-id="10149-304">Environment variables</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="10149-305">.NET core 2.1</span><span class="sxs-lookup"><span data-stu-id="10149-305">.NET Core 2.1</span></span>](#tab/netcore21)

`DOTNET_PACKAGES`

<span data-ttu-id="10149-306">Pakiet główny pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="10149-306">The primary package cache.</span></span> <span data-ttu-id="10149-307">Jeśli nie został ustawiony, jego wartość domyślna to `$HOME/.nuget/packages` w systemach Unix lub `%HOME%\NuGet\Packages` na Windows.</span><span class="sxs-lookup"><span data-stu-id="10149-307">If not set, it defaults to `$HOME/.nuget/packages` on Unix or `%HOME%\NuGet\Packages` on Windows.</span></span>

`DOTNET_SERVICING`

<span data-ttu-id="10149-308">Określa lokalizację obsługi indeksu do użycia przez hosta udostępnionych podczas ładowania środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="10149-308">Specifies the location of the servicing index to use by the shared host when loading the runtime.</span></span>

`DOTNET_CLI_TELEMETRY_OPTOUT`

<span data-ttu-id="10149-309">Określa, czy dane dotyczące użycia narzędzia .NET Core jest zbierane i przesyłane do firmy Microsoft.</span><span class="sxs-lookup"><span data-stu-id="10149-309">Specifies whether data about the .NET Core tools usage is collected and sent to Microsoft.</span></span> <span data-ttu-id="10149-310">Ustaw `true` można zrezygnować z funkcji danych telemetrycznych (wartości `true`, `1`, lub `yes` zaakceptowane).</span><span class="sxs-lookup"><span data-stu-id="10149-310">Set to `true` to opt-out of the telemetry feature (values `true`, `1`, or `yes` accepted).</span></span> <span data-ttu-id="10149-311">W przeciwnym wypadku ustaw `false` można zdecydować się na funkcje telemetrii (wartości `false`, `0`, lub `no` zaakceptowane).</span><span class="sxs-lookup"><span data-stu-id="10149-311">Otherwise, set to `false` to opt into the telemetry features (values `false`, `0`, or `no` accepted).</span></span> <span data-ttu-id="10149-312">Jeśli nie jest ustawiona, wartość domyślna to `false` i funkcja telemetrii jest aktywna.</span><span class="sxs-lookup"><span data-stu-id="10149-312">If not set, the default is `false` and the telemetry feature is active.</span></span>

`DOTNET_MULTILEVEL_LOOKUP`

<span data-ttu-id="10149-313">Określa, czy środowiska uruchomieniowego, udostępnionej platformy lub zestawu SDK platformy .NET Core nie są rozwiązane z globalnej lokalizacji.</span><span class="sxs-lookup"><span data-stu-id="10149-313">Specifies whether .NET Core runtime, shared framework, or SDK are resolved from the global location.</span></span> <span data-ttu-id="10149-314">Jeśli nie został ustawiony, jego wartość domyślna to `true`.</span><span class="sxs-lookup"><span data-stu-id="10149-314">If not set, it defaults to `true`.</span></span> <span data-ttu-id="10149-315">Ustaw `false` rozwiązania z globalnej lokalizacji i izolowanych instalacji platformy .NET Core (wartości `0` lub `false` są akceptowane).</span><span class="sxs-lookup"><span data-stu-id="10149-315">Set to `false` to not resolve from the global location and have isolated .NET Core installations (values `0` or `false` are accepted).</span></span> <span data-ttu-id="10149-316">Aby uzyskać więcej informacji na temat wyszukiwania wielopoziomowe zobacz [wyszukiwania SharedFX wielopoziomowymi](https://github.com/dotnet/core-setup/blob/master/Documentation/design-docs/multilevel-sharedfx-lookup.md).</span><span class="sxs-lookup"><span data-stu-id="10149-316">For more information about multi-level lookup, see [Multi-level SharedFX Lookup](https://github.com/dotnet/core-setup/blob/master/Documentation/design-docs/multilevel-sharedfx-lookup.md).</span></span>

`DOTNET_ROLL_FORWARD_ON_NO_CANDIDATE_FX`

<span data-ttu-id="10149-317">Wyłącza wersja pomocnicza przenoszenie do przodu, jeśli ustawiono `0`.</span><span class="sxs-lookup"><span data-stu-id="10149-317">Disables minor version roll forward, if set to `0`.</span></span> <span data-ttu-id="10149-318">Aby uzyskać więcej informacji, zobacz [uaktualniane](../whats-new/dotnet-core-2-1.md#roll-forward).</span><span class="sxs-lookup"><span data-stu-id="10149-318">For more information, see [Roll forward](../whats-new/dotnet-core-2-1.md#roll-forward).</span></span>

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="10149-319">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="10149-319">.NET Core 2.0</span></span>](#tab/netcore20)

`DOTNET_PACKAGES`

<span data-ttu-id="10149-320">Pakiet główny pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="10149-320">The primary package cache.</span></span> <span data-ttu-id="10149-321">Jeśli nie został ustawiony, jego wartość domyślna to `$HOME/.nuget/packages` w systemach Unix lub `%HOME%\NuGet\Packages` na Windows.</span><span class="sxs-lookup"><span data-stu-id="10149-321">If not set, it defaults to `$HOME/.nuget/packages` on Unix or `%HOME%\NuGet\Packages` on Windows.</span></span>

`DOTNET_SERVICING`

<span data-ttu-id="10149-322">Określa lokalizację obsługi indeksu do użycia przez hosta udostępnionych podczas ładowania środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="10149-322">Specifies the location of the servicing index to use by the shared host when loading the runtime.</span></span>

`DOTNET_CLI_TELEMETRY_OPTOUT`

<span data-ttu-id="10149-323">Określa, czy dane dotyczące użycia narzędzia .NET Core jest zbierane i przesyłane do firmy Microsoft.</span><span class="sxs-lookup"><span data-stu-id="10149-323">Specifies whether data about the .NET Core tools usage is collected and sent to Microsoft.</span></span> <span data-ttu-id="10149-324">Ustaw `true` można zrezygnować z funkcji danych telemetrycznych (wartości `true`, `1`, lub `yes` zaakceptowane).</span><span class="sxs-lookup"><span data-stu-id="10149-324">Set to `true` to opt-out of the telemetry feature (values `true`, `1`, or `yes` accepted).</span></span> <span data-ttu-id="10149-325">W przeciwnym wypadku ustaw `false` można zdecydować się na funkcje telemetrii (wartości `false`, `0`, lub `no` zaakceptowane).</span><span class="sxs-lookup"><span data-stu-id="10149-325">Otherwise, set to `false` to opt into the telemetry features (values `false`, `0`, or `no` accepted).</span></span> <span data-ttu-id="10149-326">Jeśli nie jest ustawiona, wartość domyślna to `false` i funkcja telemetrii jest aktywna.</span><span class="sxs-lookup"><span data-stu-id="10149-326">If not set, the default is `false` and the telemetry feature is active.</span></span>

`DOTNET_MULTILEVEL_LOOKUP`

<span data-ttu-id="10149-327">Określa, czy środowiska uruchomieniowego, udostępnionej platformy lub zestawu SDK platformy .NET Core nie są rozwiązane z globalnej lokalizacji.</span><span class="sxs-lookup"><span data-stu-id="10149-327">Specifies whether .NET Core runtime, shared framework, or SDK are resolved from the global location.</span></span> <span data-ttu-id="10149-328">Jeśli nie został ustawiony, jego wartość domyślna to `true`.</span><span class="sxs-lookup"><span data-stu-id="10149-328">If not set, it defaults to `true`.</span></span> <span data-ttu-id="10149-329">Ustaw `false` rozwiązania z globalnej lokalizacji i izolowanych instalacji platformy .NET Core (wartości `0` lub `false` są akceptowane).</span><span class="sxs-lookup"><span data-stu-id="10149-329">Set to `false` to not resolve from the global location and have isolated .NET Core installations (values `0` or `false` are accepted).</span></span> <span data-ttu-id="10149-330">Aby uzyskać więcej informacji na temat wyszukiwania wielopoziomowe zobacz [wyszukiwania SharedFX wielopoziomowymi](https://github.com/dotnet/core-setup/blob/master/Documentation/design-docs/multilevel-sharedfx-lookup.md).</span><span class="sxs-lookup"><span data-stu-id="10149-330">For more information about multi-level lookup, see [Multi-level SharedFX Lookup](https://github.com/dotnet/core-setup/blob/master/Documentation/design-docs/multilevel-sharedfx-lookup.md).</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="10149-331">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="10149-331">.NET Core 1.x</span></span>](#tab/netcore1x)

`DOTNET_PACKAGES`

<span data-ttu-id="10149-332">Pakiet główny pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="10149-332">The primary package cache.</span></span> <span data-ttu-id="10149-333">Jeśli nie został ustawiony, jego wartość domyślna to `$HOME/.nuget/packages` w systemach Unix lub `%HOME%\NuGet\Packages` na Windows.</span><span class="sxs-lookup"><span data-stu-id="10149-333">If not set, it defaults to `$HOME/.nuget/packages` on Unix or `%HOME%\NuGet\Packages` on Windows.</span></span>

`DOTNET_SERVICING`

<span data-ttu-id="10149-334">Określa lokalizację obsługi indeksu do użycia przez hosta udostępnionych podczas ładowania środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="10149-334">Specifies the location of the servicing index to use by the shared host when loading the runtime.</span></span>

`DOTNET_CLI_TELEMETRY_OPTOUT`

<span data-ttu-id="10149-335">Określa, czy dane dotyczące użycia narzędzia .NET Core jest zbierane i przesyłane do firmy Microsoft.</span><span class="sxs-lookup"><span data-stu-id="10149-335">Specifies whether data about the .NET Core tools usage is collected and sent to Microsoft.</span></span> <span data-ttu-id="10149-336">Ustaw `true` można zrezygnować z funkcji danych telemetrycznych (wartości `true`, `1`, lub `yes` zaakceptowane).</span><span class="sxs-lookup"><span data-stu-id="10149-336">Set to `true` to opt-out of the telemetry feature (values `true`, `1`, or `yes` accepted).</span></span> <span data-ttu-id="10149-337">W przeciwnym wypadku ustaw `false` można zdecydować się na funkcje telemetrii (wartości `false`, `0`, lub `no` zaakceptowane).</span><span class="sxs-lookup"><span data-stu-id="10149-337">Otherwise, set to `false` to opt into the telemetry features (values `false`, `0`, or `no` accepted).</span></span> <span data-ttu-id="10149-338">Jeśli nie jest ustawiona, wartość domyślna to `false` i funkcja telemetrii jest aktywna.</span><span class="sxs-lookup"><span data-stu-id="10149-338">If not set, the default is `false` and the telemetry feature is active.</span></span>

---
