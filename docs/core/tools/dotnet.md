---
title: dotnet — polecenie
description: Dowiedz się więcej na temat polecenia dotnet (sterownika generycznego dla narzędzi interfejs wiersza polecenia platformy .NET Core) i jego użycia.
ms.date: 06/04/2018
ms.openlocfilehash: 61542a3fff8bba6e2c3e55a4db5a746620d79ca1
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/31/2019
ms.locfileid: "70202508"
---
# <a name="dotnet-command"></a><span data-ttu-id="28796-103">dotnet — polecenie</span><span class="sxs-lookup"><span data-stu-id="28796-103">dotnet command</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="28796-104">Nazwa</span><span class="sxs-lookup"><span data-stu-id="28796-104">Name</span></span>

<span data-ttu-id="28796-105">`dotnet`-Narzędzie do zarządzania kodem źródłowym i plikami binarnymi platformy .NET.</span><span class="sxs-lookup"><span data-stu-id="28796-105">`dotnet` - A tool for managing .NET source code and binaries.</span></span>

## <a name="synopsis"></a><span data-ttu-id="28796-106">Streszczenie</span><span class="sxs-lookup"><span data-stu-id="28796-106">Synopsis</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="28796-107">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="28796-107">.NET Core 2.1</span></span>](#tab/netcore21)

```console
dotnet [command] [arguments] [--additional-deps] [--additionalprobingpath] [--depsfile]
    [-d|--diagnostics] [--fx-version] [-h|--help] [--info] [--list-runtimes] [--list-sdks] [--roll-forward-on-no-candidate-fx] [--runtimeconfig] [-v|--verbosity] [--version]
```

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="28796-108">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="28796-108">.NET Core 2.0</span></span>](#tab/netcore20)

```console
dotnet [command] [arguments] [--additional-deps] [--additionalprobingpath] [--depsfile]
    [-d|--diagnostics] [--fx-version] [-h|--help] [--info] [--roll-forward-on-no-candidate-fx]
    [--runtimeconfig] [-v|--verbosity] [--version]
```

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="28796-109">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="28796-109">.NET Core 1.x</span></span>](#tab/netcore1x)

```console
dotnet [command] [arguments] [--additionalprobingpath] [--depsfile] [-d|--diagnostics]
    [--fx-version] [-h|--help] [--info] [--runtimeconfig] [-v|--verbosity] [--version]
```

---

## <a name="description"></a><span data-ttu-id="28796-110">Opis</span><span class="sxs-lookup"><span data-stu-id="28796-110">Description</span></span>

<span data-ttu-id="28796-111">`dotnet`jest narzędziem do zarządzania kodem źródłowym i plikami binarnymi platformy .NET.</span><span class="sxs-lookup"><span data-stu-id="28796-111">`dotnet` is a tool for managing .NET source code and binaries.</span></span> <span data-ttu-id="28796-112">Udostępnia polecenia wykonujące określone zadania, takie jak [`dotnet build`](dotnet-build.md) i. [`dotnet run`](dotnet-run.md)</span><span class="sxs-lookup"><span data-stu-id="28796-112">It exposes commands that perform specific tasks, such as [`dotnet build`](dotnet-build.md) and [`dotnet run`](dotnet-run.md).</span></span> <span data-ttu-id="28796-113">Każde polecenie definiuje własne argumenty.</span><span class="sxs-lookup"><span data-stu-id="28796-113">Each command defines its own arguments.</span></span> <span data-ttu-id="28796-114">Wpisz `--help` po każdym poleceniu, aby uzyskać dostęp do krótkiej dokumentacji pomocy.</span><span class="sxs-lookup"><span data-stu-id="28796-114">Type `--help` after each command to access brief help documentation.</span></span>

<span data-ttu-id="28796-115">`dotnet`może służyć do uruchamiania aplikacji przez określenie biblioteki DLL aplikacji, takiej jak `dotnet myapp.dll`.</span><span class="sxs-lookup"><span data-stu-id="28796-115">`dotnet` can be used to run applications, by specifying an application DLL, such as `dotnet myapp.dll`.</span></span> <span data-ttu-id="28796-116">Zobacz [wdrażanie aplikacji .NET Core](../deploying/index.md) w celu uzyskania informacji na temat opcji wdrażania.</span><span class="sxs-lookup"><span data-stu-id="28796-116">See [.NET Core application deployment](../deploying/index.md) for to learn about deployment options.</span></span>

## <a name="options"></a><span data-ttu-id="28796-117">Opcje</span><span class="sxs-lookup"><span data-stu-id="28796-117">Options</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="28796-118">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="28796-118">.NET Core 2.1</span></span>](#tab/netcore21)

`--additional-deps <PATH>`

<span data-ttu-id="28796-119">Ścieżka do dodatkowego pliku *. deps. JSON* .</span><span class="sxs-lookup"><span data-stu-id="28796-119">Path to an additional *.deps.json* file.</span></span>

`--additionalprobingpath <PATH>`

<span data-ttu-id="28796-120">Ścieżka zawierająca zasady i zestawy do sondowania.</span><span class="sxs-lookup"><span data-stu-id="28796-120">Path containing probing policy and assemblies to probe.</span></span>

`--depsfile`

<span data-ttu-id="28796-121">Ścieżka do pliku *deps. JSON* .</span><span class="sxs-lookup"><span data-stu-id="28796-121">Path to a *deps.json* file.</span></span>

<span data-ttu-id="28796-122">Plik *deps. JSON* zawiera listę zależności, zależności kompilacji i informacje o wersji używane do rozwiązywania konfliktów zestawów.</span><span class="sxs-lookup"><span data-stu-id="28796-122">A *deps.json* file contains a list of dependencies, compilation dependencies and version information used to address assembly conflicts.</span></span> <span data-ttu-id="28796-123">Aby uzyskać więcej informacji na temat tego pliku, zobacz [pliki konfiguracji środowiska uruchomieniowego](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md) w serwisie GitHub.</span><span class="sxs-lookup"><span data-stu-id="28796-123">For more information about this file, see [Runtime Configuration Files](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md) on GitHub.</span></span>

`-d|--diagnostics`

<span data-ttu-id="28796-124">Włącza diagnostykę danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="28796-124">Enables diagnostic output.</span></span>

`--fx-version <VERSION>`

<span data-ttu-id="28796-125">Wersja środowiska uruchomieniowego platformy .NET Core do użycia w celu uruchomienia aplikacji.</span><span class="sxs-lookup"><span data-stu-id="28796-125">Version of the .NET Core runtime to use to run the application.</span></span>

`-h|--help`

<span data-ttu-id="28796-126">Drukuje dokumentację dla danego polecenia, na przykład `dotnet build --help`.</span><span class="sxs-lookup"><span data-stu-id="28796-126">Prints out documentation for a given command, such as `dotnet build --help`.</span></span> <span data-ttu-id="28796-127">`dotnet --help`Drukuje listę dostępnych poleceń.</span><span class="sxs-lookup"><span data-stu-id="28796-127">`dotnet --help` prints a list of available commands.</span></span>

`--info`

<span data-ttu-id="28796-128">Drukuje szczegółowe informacje na temat instalacji programu .NET Core i środowiska maszynowego, takiego jak bieżący system operacyjny, i zatwierdzania SHA dla wersji .NET Core.</span><span class="sxs-lookup"><span data-stu-id="28796-128">Prints out detailed information about a .NET Core installation and the machine environment, such as the current operating system, and commit SHA of the .NET Core version.</span></span>

`--list-runtimes`

<span data-ttu-id="28796-129">Wyświetla zainstalowane środowiska uruchomieniowe platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="28796-129">Displays the installed .NET Core runtimes.</span></span>

`--list-sdks`

<span data-ttu-id="28796-130">Wyświetla zainstalowane zestawy SDK platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="28796-130">Displays the installed .NET Core SDKs.</span></span>

`--roll-forward-on-no-candidate-fx <N>`

<span data-ttu-id="28796-131">Definiuje zachowanie, gdy wymagana architektura udostępniona jest niedostępna.</span><span class="sxs-lookup"><span data-stu-id="28796-131">Defines behavior when the required shared framework is not available.</span></span> <span data-ttu-id="28796-132">`N` może być:</span><span class="sxs-lookup"><span data-stu-id="28796-132">`N` can be:</span></span>
* <span data-ttu-id="28796-133">`0`-Wyłącz parzystą wersję pomocniczą do przodu.</span><span class="sxs-lookup"><span data-stu-id="28796-133">`0` - Disable even minor version roll forward.</span></span>
* <span data-ttu-id="28796-134">`1`— Przewinięcie do wersji pomocniczej, ale nie w wersji głównej.</span><span class="sxs-lookup"><span data-stu-id="28796-134">`1` - Roll forward on minor version, but not on major version.</span></span> <span data-ttu-id="28796-135">Jest to zachowanie domyślne.</span><span class="sxs-lookup"><span data-stu-id="28796-135">This is the default behavior.</span></span>
* <span data-ttu-id="28796-136">`2`— Przewinięcie do przodu w wersjach pomocniczych i głównych.</span><span class="sxs-lookup"><span data-stu-id="28796-136">`2` - Roll forward on minor and major versions.</span></span>

 <span data-ttu-id="28796-137">Aby uzyskać więcej informacji, zobacz [przewinięcie do przodu](../whats-new/dotnet-core-2-1.md#roll-forward).</span><span class="sxs-lookup"><span data-stu-id="28796-137">For more information, see [Roll forward](../whats-new/dotnet-core-2-1.md#roll-forward).</span></span>

`--runtimeconfig`

<span data-ttu-id="28796-138">Ścieżka do pliku *runtimeconfig. JSON* .</span><span class="sxs-lookup"><span data-stu-id="28796-138">Path to a *runtimeconfig.json* file.</span></span>

<span data-ttu-id="28796-139">Plik *runtimeconfig. JSON* to plik konfiguracji zawierający ustawienia konfiguracji środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="28796-139">A *runtimeconfig.json* file is a configuration file containing runtime configuration settings.</span></span> <span data-ttu-id="28796-140">Aby uzyskać więcej informacji, zobacz [pliki konfiguracji środowiska uruchomieniowego](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md) w serwisie GitHub.</span><span class="sxs-lookup"><span data-stu-id="28796-140">For more information, see [Runtime Configuration Files](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md) on GitHub.</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="28796-141">Ustawia poziom szczegółowości polecenia.</span><span class="sxs-lookup"><span data-stu-id="28796-141">Sets the verbosity level of the command.</span></span> <span data-ttu-id="28796-142">Dozwolone wartości to `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`i .`diag[nostic]`</span><span class="sxs-lookup"><span data-stu-id="28796-142">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="28796-143">Nieobsługiwane w każdym poleceniu; Aby określić, czy ta opcja jest dostępna, zobacz określoną stronę poleceń.</span><span class="sxs-lookup"><span data-stu-id="28796-143">Not supported in every command; see specific command page to determine if this option is available.</span></span>

`--version`

<span data-ttu-id="28796-144">Drukuje używaną wersję zestaw .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="28796-144">Prints out the version of the .NET Core SDK in use.</span></span>

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="28796-145">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="28796-145">.NET Core 2.0</span></span>](#tab/netcore20)

`--additional-deps <PATH>`

<span data-ttu-id="28796-146">Ścieżka do dodatkowego pliku *. deps. JSON* .</span><span class="sxs-lookup"><span data-stu-id="28796-146">Path to an additional *.deps.json* file.</span></span>

`--additionalprobingpath <PATH>`

<span data-ttu-id="28796-147">Ścieżka zawierająca zasady i zestawy do sondowania.</span><span class="sxs-lookup"><span data-stu-id="28796-147">Path containing probing policy and assemblies to probe.</span></span>

`--depsfile`

<span data-ttu-id="28796-148">Ścieżka do pliku *deps. JSON* .</span><span class="sxs-lookup"><span data-stu-id="28796-148">Path to a *deps.json* file.</span></span>

<span data-ttu-id="28796-149">Plik *deps. JSON* zawiera listę zależności, zależności kompilacji i informacje o wersji używane do rozwiązywania konfliktów zestawów.</span><span class="sxs-lookup"><span data-stu-id="28796-149">A *deps.json* file contains a list of dependencies, compilation dependencies and version information used to address assembly conflicts.</span></span> <span data-ttu-id="28796-150">Aby uzyskać więcej informacji na temat tego pliku, zobacz [pliki konfiguracji środowiska uruchomieniowego w serwisie GitHub](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md).</span><span class="sxs-lookup"><span data-stu-id="28796-150">For more details on this file, see [Runtime Configuration Files on GitHub](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md).</span></span>

`-d|--diagnostics`

<span data-ttu-id="28796-151">Włącza diagnostykę danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="28796-151">Enables diagnostic output.</span></span>

`--fx-version <VERSION>`

<span data-ttu-id="28796-152">Wersja środowiska uruchomieniowego platformy .NET Core do użycia w celu uruchomienia aplikacji.</span><span class="sxs-lookup"><span data-stu-id="28796-152">Version of the .NET Core runtime to use to run the application.</span></span>

`-h|--help`

<span data-ttu-id="28796-153">Drukuje dokumentację dla danego polecenia, na przykład `dotnet build --help`.</span><span class="sxs-lookup"><span data-stu-id="28796-153">Prints out documentation for a given command, such as `dotnet build --help`.</span></span> <span data-ttu-id="28796-154">`dotnet --help`Drukuje listę dostępnych poleceń.</span><span class="sxs-lookup"><span data-stu-id="28796-154">`dotnet --help` prints a list of available commands.</span></span>

`--info`

<span data-ttu-id="28796-155">Drukuje szczegółowe informacje na temat instalacji programu .NET Core i środowiska maszynowego, takiego jak bieżący system operacyjny, i zatwierdzania SHA dla wersji .NET Core.</span><span class="sxs-lookup"><span data-stu-id="28796-155">Prints out detailed information about a .NET Core installation and the machine environment, such as the current operating system, and commit SHA of the .NET Core version.</span></span>

`--roll-forward-on-no-candidate-fx`

 <span data-ttu-id="28796-156">Wyłącza dodatkową wersję do przodu, jeśli jest ustawiona `0`na.</span><span class="sxs-lookup"><span data-stu-id="28796-156">Disables minor version roll forward, if set to `0`.</span></span> <span data-ttu-id="28796-157">Aby uzyskać więcej informacji, zobacz [przewinięcie do przodu](../whats-new/dotnet-core-2-1.md#roll-forward).</span><span class="sxs-lookup"><span data-stu-id="28796-157">For more information, see [Roll forward](../whats-new/dotnet-core-2-1.md#roll-forward).</span></span>

`--runtimeconfig`

<span data-ttu-id="28796-158">Ścieżka do pliku *runtimeconfig. JSON* .</span><span class="sxs-lookup"><span data-stu-id="28796-158">Path to a *runtimeconfig.json* file.</span></span>

<span data-ttu-id="28796-159">Plik *runtimeconfig. JSON* to plik konfiguracji zawierający ustawienia konfiguracji środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="28796-159">A *runtimeconfig.json* file is a configuration file containing runtime configuration settings.</span></span> <span data-ttu-id="28796-160">Aby uzyskać więcej informacji, zobacz [pliki konfiguracji środowiska uruchomieniowego w serwisie GitHub](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md).</span><span class="sxs-lookup"><span data-stu-id="28796-160">For more details, see [Runtime Configuration Files on GitHub](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md).</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="28796-161">Ustawia poziom szczegółowości polecenia.</span><span class="sxs-lookup"><span data-stu-id="28796-161">Sets the verbosity level of the command.</span></span> <span data-ttu-id="28796-162">Dozwolone wartości to `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`i .`diag[nostic]`</span><span class="sxs-lookup"><span data-stu-id="28796-162">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="28796-163">Nieobsługiwane w każdym poleceniu; Aby określić, czy ta opcja jest dostępna, zobacz określoną stronę poleceń.</span><span class="sxs-lookup"><span data-stu-id="28796-163">Not supported in every command; see specific command page to determine if this option is available.</span></span>

`--version`

<span data-ttu-id="28796-164">Drukuje używaną wersję zestaw .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="28796-164">Prints out the version of the .NET Core SDK in use.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="28796-165">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="28796-165">.NET Core 1.x</span></span>](#tab/netcore1x)

`--additionalprobingpath <PATH>`

<span data-ttu-id="28796-166">Ścieżka zawierająca zasady i zestawy do sondowania.</span><span class="sxs-lookup"><span data-stu-id="28796-166">Path containing probing policy and assemblies to probe.</span></span>

`--depsfile`

<span data-ttu-id="28796-167">Ścieżka do pliku *deps. JSON* .</span><span class="sxs-lookup"><span data-stu-id="28796-167">Path to a *deps.json* file.</span></span>

<span data-ttu-id="28796-168">Plik *deps. JSON* zawiera listę zależności, zależności kompilacji i informacje o wersji używane do rozwiązywania konfliktów zestawów.</span><span class="sxs-lookup"><span data-stu-id="28796-168">A *deps.json* file contains a list of dependencies, compilation dependencies and version information used to address assembly conflicts.</span></span> <span data-ttu-id="28796-169">Aby uzyskać więcej informacji na temat tego pliku, zobacz [pliki konfiguracji środowiska uruchomieniowego w serwisie GitHub](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md).</span><span class="sxs-lookup"><span data-stu-id="28796-169">For more details on this file, see [Runtime Configuration Files on GitHub](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md).</span></span>

`-d|--diagnostics`

<span data-ttu-id="28796-170">Włącza diagnostykę danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="28796-170">Enables diagnostic output.</span></span>

`--fx-version <VERSION>`

<span data-ttu-id="28796-171">Wersja środowiska uruchomieniowego platformy .NET Core do użycia w celu uruchomienia aplikacji.</span><span class="sxs-lookup"><span data-stu-id="28796-171">Version of the .NET Core runtime to use to run the application.</span></span>

`-h|--help`

<span data-ttu-id="28796-172">Drukuje dokumentację dla danego polecenia, na przykład `dotnet build --help`.</span><span class="sxs-lookup"><span data-stu-id="28796-172">Prints out documentation for a given command, such as `dotnet build --help`.</span></span> <span data-ttu-id="28796-173">`dotnet --help`Drukuje listę dostępnych poleceń.</span><span class="sxs-lookup"><span data-stu-id="28796-173">`dotnet --help` prints a list of available commands.</span></span>

`--info`

<span data-ttu-id="28796-174">Drukuje szczegółowe informacje na temat instalacji programu .NET Core i środowiska maszynowego, takiego jak bieżący system operacyjny, i zatwierdzania SHA dla wersji .NET Core.</span><span class="sxs-lookup"><span data-stu-id="28796-174">Prints out detailed information about a .NET Core installation and the machine environment, such as the current operating system, and commit SHA of the .NET Core version.</span></span>

`--runtimeconfig`

<span data-ttu-id="28796-175">Ścieżka do pliku *runtimeconfig. JSON* .</span><span class="sxs-lookup"><span data-stu-id="28796-175">Path to a *runtimeconfig.json* file.</span></span>

<span data-ttu-id="28796-176">Plik *runtimeconfig. JSON* to plik konfiguracji zawierający ustawienia konfiguracji środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="28796-176">A *runtimeconfig.json* file is a configuration file containing runtime configuration settings.</span></span> <span data-ttu-id="28796-177">Aby uzyskać więcej informacji, zobacz [pliki konfiguracji środowiska uruchomieniowego w serwisie GitHub](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md).</span><span class="sxs-lookup"><span data-stu-id="28796-177">For more details, see [Runtime Configuration Files on GitHub](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md).</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="28796-178">Ustawia poziom szczegółowości polecenia.</span><span class="sxs-lookup"><span data-stu-id="28796-178">Sets the verbosity level of the command.</span></span> <span data-ttu-id="28796-179">Dozwolone wartości to `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`i .`diag[nostic]`</span><span class="sxs-lookup"><span data-stu-id="28796-179">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="28796-180">Nieobsługiwane w każdym poleceniu; Aby określić, czy ta opcja jest dostępna, zobacz określoną stronę poleceń.</span><span class="sxs-lookup"><span data-stu-id="28796-180">Not supported in every command; see specific command page to determine if this option is available.</span></span>

`--version`

<span data-ttu-id="28796-181">Drukuje używaną wersję zestaw .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="28796-181">Prints out the version of the .NET Core SDK in use.</span></span>

---

## <a name="dotnet-commands"></a><span data-ttu-id="28796-182">Polecenia dotnet</span><span class="sxs-lookup"><span data-stu-id="28796-182">dotnet commands</span></span>

### <a name="general"></a><span data-ttu-id="28796-183">Ogólne</span><span class="sxs-lookup"><span data-stu-id="28796-183">General</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="28796-184">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="28796-184">.NET Core 2.1</span></span>](#tab/netcore21)

| <span data-ttu-id="28796-185">Polecenie</span><span class="sxs-lookup"><span data-stu-id="28796-185">Command</span></span>                                       | <span data-ttu-id="28796-186">Funkcja</span><span class="sxs-lookup"><span data-stu-id="28796-186">Function</span></span>                                                            |
| --------------------------------------------- | ------------------------------------------------------------------- |
| [<span data-ttu-id="28796-187">dotnet build</span><span class="sxs-lookup"><span data-stu-id="28796-187">dotnet build</span></span>](dotnet-build.md)               | <span data-ttu-id="28796-188">Kompiluje aplikację platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="28796-188">Builds a .NET Core application.</span></span>                                     |
| [<span data-ttu-id="28796-189">dotnet build-server</span><span class="sxs-lookup"><span data-stu-id="28796-189">dotnet build-server</span></span>](dotnet-build-server.md) | <span data-ttu-id="28796-190">Współdziała z serwerami uruchomionymi przez kompilację.</span><span class="sxs-lookup"><span data-stu-id="28796-190">Interacts with servers started by a build.</span></span>                          |
| [<span data-ttu-id="28796-191">dotnet clean</span><span class="sxs-lookup"><span data-stu-id="28796-191">dotnet clean</span></span>](dotnet-clean.md)               | <span data-ttu-id="28796-192">Czyste dane wyjściowe kompilacji.</span><span class="sxs-lookup"><span data-stu-id="28796-192">Clean build outputs.</span></span>                                                |
| [<span data-ttu-id="28796-193">dotnet help</span><span class="sxs-lookup"><span data-stu-id="28796-193">dotnet help</span></span>](dotnet-help.md)                 | <span data-ttu-id="28796-194">Przedstawia bardziej szczegółową dokumentację dla polecenia w trybie online.</span><span class="sxs-lookup"><span data-stu-id="28796-194">Shows more detailed documentation online for the command.</span></span>           |
| [<span data-ttu-id="28796-195">dotnet migrate</span><span class="sxs-lookup"><span data-stu-id="28796-195">dotnet migrate</span></span>](dotnet-migrate.md)           | <span data-ttu-id="28796-196">Migruje prawidłowy projekt w wersji zapoznawczej 2 do projektu zestaw .NET Core SDK 1,0.</span><span class="sxs-lookup"><span data-stu-id="28796-196">Migrates a valid Preview 2 project to a .NET Core SDK 1.0 project.</span></span>  |
| [<span data-ttu-id="28796-197">dotnet msbuild</span><span class="sxs-lookup"><span data-stu-id="28796-197">dotnet msbuild</span></span>](dotnet-msbuild.md)           | <span data-ttu-id="28796-198">Zapewnia dostęp do wiersza polecenia programu MSBuild.</span><span class="sxs-lookup"><span data-stu-id="28796-198">Provides access to the MSBuild command line.</span></span>                        |
| [<span data-ttu-id="28796-199">dotnet new</span><span class="sxs-lookup"><span data-stu-id="28796-199">dotnet new</span></span>](dotnet-new.md)                   | <span data-ttu-id="28796-200">Inicjuje projekt C# lub F# dla danego szablonu.</span><span class="sxs-lookup"><span data-stu-id="28796-200">Initializes a C# or F# project for a given template.</span></span>                |
| [<span data-ttu-id="28796-201">dotnet pack</span><span class="sxs-lookup"><span data-stu-id="28796-201">dotnet pack</span></span>](dotnet-pack.md)                 | <span data-ttu-id="28796-202">Tworzy pakiet NuGet kodu.</span><span class="sxs-lookup"><span data-stu-id="28796-202">Creates a NuGet package of your code.</span></span>                               |
| [<span data-ttu-id="28796-203">dotnet publish</span><span class="sxs-lookup"><span data-stu-id="28796-203">dotnet publish</span></span>](dotnet-publish.md)           | <span data-ttu-id="28796-204">Publikuje zależne od programu .NET Framework lub samodzielną aplikację.</span><span class="sxs-lookup"><span data-stu-id="28796-204">Publishes a .NET framework-dependent or self-contained application.</span></span> |
| [<span data-ttu-id="28796-205">dotnet restore</span><span class="sxs-lookup"><span data-stu-id="28796-205">dotnet restore</span></span>](dotnet-restore.md)           | <span data-ttu-id="28796-206">Przywraca zależności dla danej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="28796-206">Restores the dependencies for a given application.</span></span>                  |
| [<span data-ttu-id="28796-207">dotnet run</span><span class="sxs-lookup"><span data-stu-id="28796-207">dotnet run</span></span>](dotnet-run.md)                   | <span data-ttu-id="28796-208">Uruchamia aplikację ze źródła.</span><span class="sxs-lookup"><span data-stu-id="28796-208">Runs the application from source.</span></span>                                   |
| [<span data-ttu-id="28796-209">dotnet sln</span><span class="sxs-lookup"><span data-stu-id="28796-209">dotnet sln</span></span>](dotnet-sln.md)                   | <span data-ttu-id="28796-210">Opcje dodawania, usuwania i wyświetlania listy projektów w pliku rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="28796-210">Options to add, remove, and list projects in a solution file.</span></span>       |
| [<span data-ttu-id="28796-211">dotnet store</span><span class="sxs-lookup"><span data-stu-id="28796-211">dotnet store</span></span>](dotnet-store.md)               | <span data-ttu-id="28796-212">Przechowuje zestawy w magazynie pakietów środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="28796-212">Stores assemblies in the runtime package store.</span></span>                     |
| [<span data-ttu-id="28796-213">dotnet test</span><span class="sxs-lookup"><span data-stu-id="28796-213">dotnet test</span></span>](dotnet-test.md)                 | <span data-ttu-id="28796-214">Uruchamia testy przy użyciu modułu uruchamiającego testy.</span><span class="sxs-lookup"><span data-stu-id="28796-214">Runs tests using a test runner.</span></span>                                     |

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="28796-215">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="28796-215">.NET Core 2.0</span></span>](#tab/netcore20)

| <span data-ttu-id="28796-216">Polecenie</span><span class="sxs-lookup"><span data-stu-id="28796-216">Command</span></span>                             | <span data-ttu-id="28796-217">Funkcja</span><span class="sxs-lookup"><span data-stu-id="28796-217">Function</span></span>                                                            |
| ----------------------------------- | ------------------------------------------------------------------- |
| [<span data-ttu-id="28796-218">dotnet build</span><span class="sxs-lookup"><span data-stu-id="28796-218">dotnet build</span></span>](dotnet-build.md)     | <span data-ttu-id="28796-219">Kompiluje aplikację platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="28796-219">Builds a .NET Core application.</span></span>                                     |
| [<span data-ttu-id="28796-220">dotnet clean</span><span class="sxs-lookup"><span data-stu-id="28796-220">dotnet clean</span></span>](dotnet-clean.md)     | <span data-ttu-id="28796-221">Czyste dane wyjściowe kompilacji.</span><span class="sxs-lookup"><span data-stu-id="28796-221">Clean build outputs.</span></span>                                              |
| [<span data-ttu-id="28796-222">dotnet help</span><span class="sxs-lookup"><span data-stu-id="28796-222">dotnet help</span></span>](dotnet-help.md)       | <span data-ttu-id="28796-223">Przedstawia bardziej szczegółową dokumentację dla polecenia w trybie online.</span><span class="sxs-lookup"><span data-stu-id="28796-223">Shows more detailed documentation online for the command.</span></span>           |
| [<span data-ttu-id="28796-224">dotnet migrate</span><span class="sxs-lookup"><span data-stu-id="28796-224">dotnet migrate</span></span>](dotnet-migrate.md) | <span data-ttu-id="28796-225">Migruje prawidłowy projekt w wersji zapoznawczej 2 do projektu zestaw .NET Core SDK 1,0.</span><span class="sxs-lookup"><span data-stu-id="28796-225">Migrates a valid Preview 2 project to a .NET Core SDK 1.0 project.</span></span>  |
| [<span data-ttu-id="28796-226">dotnet msbuild</span><span class="sxs-lookup"><span data-stu-id="28796-226">dotnet msbuild</span></span>](dotnet-msbuild.md) | <span data-ttu-id="28796-227">Zapewnia dostęp do wiersza polecenia programu MSBuild.</span><span class="sxs-lookup"><span data-stu-id="28796-227">Provides access to the MSBuild command line.</span></span>                        |
| [<span data-ttu-id="28796-228">dotnet new</span><span class="sxs-lookup"><span data-stu-id="28796-228">dotnet new</span></span>](dotnet-new.md)         | <span data-ttu-id="28796-229">Inicjuje projekt C# lub F# dla danego szablonu.</span><span class="sxs-lookup"><span data-stu-id="28796-229">Initializes a C# or F# project for a given template.</span></span>                |
| [<span data-ttu-id="28796-230">dotnet pack</span><span class="sxs-lookup"><span data-stu-id="28796-230">dotnet pack</span></span>](dotnet-pack.md)       | <span data-ttu-id="28796-231">Tworzy pakiet NuGet kodu.</span><span class="sxs-lookup"><span data-stu-id="28796-231">Creates a NuGet package of your code.</span></span>                               |
| [<span data-ttu-id="28796-232">dotnet publish</span><span class="sxs-lookup"><span data-stu-id="28796-232">dotnet publish</span></span>](dotnet-publish.md) | <span data-ttu-id="28796-233">Publikuje zależne od programu .NET Framework lub samodzielną aplikację.</span><span class="sxs-lookup"><span data-stu-id="28796-233">Publishes a .NET framework-dependent or self-contained application.</span></span> |
| [<span data-ttu-id="28796-234">dotnet restore</span><span class="sxs-lookup"><span data-stu-id="28796-234">dotnet restore</span></span>](dotnet-restore.md) | <span data-ttu-id="28796-235">Przywraca zależności dla danej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="28796-235">Restores the dependencies for a given application.</span></span>                  |
| [<span data-ttu-id="28796-236">dotnet run</span><span class="sxs-lookup"><span data-stu-id="28796-236">dotnet run</span></span>](dotnet-run.md)         | <span data-ttu-id="28796-237">Uruchamia aplikację ze źródła.</span><span class="sxs-lookup"><span data-stu-id="28796-237">Runs the application from source.</span></span>                                   |
| [<span data-ttu-id="28796-238">dotnet sln</span><span class="sxs-lookup"><span data-stu-id="28796-238">dotnet sln</span></span>](dotnet-sln.md)         | <span data-ttu-id="28796-239">Opcje dodawania, usuwania i wyświetlania listy projektów w pliku rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="28796-239">Options to add, remove, and list projects in a solution file.</span></span>       |
| [<span data-ttu-id="28796-240">dotnet store</span><span class="sxs-lookup"><span data-stu-id="28796-240">dotnet store</span></span>](dotnet-store.md)     | <span data-ttu-id="28796-241">Przechowuje zestawy w magazynie pakietów środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="28796-241">Stores assemblies in the runtime package store.</span></span>                     |
| [<span data-ttu-id="28796-242">dotnet test</span><span class="sxs-lookup"><span data-stu-id="28796-242">dotnet test</span></span>](dotnet-test.md)       | <span data-ttu-id="28796-243">Uruchamia testy przy użyciu modułu uruchamiającego testy.</span><span class="sxs-lookup"><span data-stu-id="28796-243">Runs tests using a test runner.</span></span>                                     |

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="28796-244">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="28796-244">.NET Core 1.x</span></span>](#tab/netcore1x)

| <span data-ttu-id="28796-245">Polecenie</span><span class="sxs-lookup"><span data-stu-id="28796-245">Command</span></span>                             | <span data-ttu-id="28796-246">Funkcja</span><span class="sxs-lookup"><span data-stu-id="28796-246">Function</span></span>                                                            |
| ----------------------------------- | ------------------------------------------------------------------- |
| [<span data-ttu-id="28796-247">dotnet build</span><span class="sxs-lookup"><span data-stu-id="28796-247">dotnet build</span></span>](dotnet-build.md)     | <span data-ttu-id="28796-248">Kompiluje aplikację platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="28796-248">Builds a .NET Core application.</span></span>                                     |
| [<span data-ttu-id="28796-249">dotnet clean</span><span class="sxs-lookup"><span data-stu-id="28796-249">dotnet clean</span></span>](dotnet-clean.md)     | <span data-ttu-id="28796-250">Czyste dane wyjściowe kompilacji.</span><span class="sxs-lookup"><span data-stu-id="28796-250">Clean build outputs.</span></span>                                              |
| [<span data-ttu-id="28796-251">dotnet migrate</span><span class="sxs-lookup"><span data-stu-id="28796-251">dotnet migrate</span></span>](dotnet-migrate.md) | <span data-ttu-id="28796-252">Migruje prawidłowy projekt w wersji zapoznawczej 2 do projektu zestaw .NET Core SDK 1,0.</span><span class="sxs-lookup"><span data-stu-id="28796-252">Migrates a valid Preview 2 project to a .NET Core SDK 1.0 project.</span></span>  |
| [<span data-ttu-id="28796-253">dotnet msbuild</span><span class="sxs-lookup"><span data-stu-id="28796-253">dotnet msbuild</span></span>](dotnet-msbuild.md) | <span data-ttu-id="28796-254">Zapewnia dostęp do wiersza polecenia programu MSBuild.</span><span class="sxs-lookup"><span data-stu-id="28796-254">Provides access to the MSBuild command line.</span></span>                        |
| [<span data-ttu-id="28796-255">dotnet new</span><span class="sxs-lookup"><span data-stu-id="28796-255">dotnet new</span></span>](dotnet-new.md)         | <span data-ttu-id="28796-256">Inicjuje projekt C# lub F# dla danego szablonu.</span><span class="sxs-lookup"><span data-stu-id="28796-256">Initializes a C# or F# project for a given template.</span></span>                |
| [<span data-ttu-id="28796-257">dotnet pack</span><span class="sxs-lookup"><span data-stu-id="28796-257">dotnet pack</span></span>](dotnet-pack.md)       | <span data-ttu-id="28796-258">Tworzy pakiet NuGet kodu.</span><span class="sxs-lookup"><span data-stu-id="28796-258">Creates a NuGet package of your code.</span></span>                               |
| [<span data-ttu-id="28796-259">dotnet publish</span><span class="sxs-lookup"><span data-stu-id="28796-259">dotnet publish</span></span>](dotnet-publish.md) | <span data-ttu-id="28796-260">Publikuje zależne od programu .NET Framework lub samodzielną aplikację.</span><span class="sxs-lookup"><span data-stu-id="28796-260">Publishes a .NET framework-dependent or self-contained application.</span></span> |
| [<span data-ttu-id="28796-261">dotnet restore</span><span class="sxs-lookup"><span data-stu-id="28796-261">dotnet restore</span></span>](dotnet-restore.md) | <span data-ttu-id="28796-262">Przywraca zależności dla danej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="28796-262">Restores the dependencies for a given application.</span></span>                  |
| [<span data-ttu-id="28796-263">dotnet run</span><span class="sxs-lookup"><span data-stu-id="28796-263">dotnet run</span></span>](dotnet-run.md)         | <span data-ttu-id="28796-264">Uruchamia aplikację ze źródła.</span><span class="sxs-lookup"><span data-stu-id="28796-264">Runs the application from source.</span></span>                                   |
| [<span data-ttu-id="28796-265">dotnet sln</span><span class="sxs-lookup"><span data-stu-id="28796-265">dotnet sln</span></span>](dotnet-sln.md)         | <span data-ttu-id="28796-266">Opcje dodawania, usuwania i wyświetlania listy projektów w pliku rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="28796-266">Options to add, remove, and list projects in a solution file.</span></span>       |
| [<span data-ttu-id="28796-267">dotnet test</span><span class="sxs-lookup"><span data-stu-id="28796-267">dotnet test</span></span>](dotnet-test.md)       | <span data-ttu-id="28796-268">Uruchamia testy przy użyciu modułu uruchamiającego testy.</span><span class="sxs-lookup"><span data-stu-id="28796-268">Runs tests using a test runner.</span></span>                                     |

---

### <a name="project-references"></a><span data-ttu-id="28796-269">Odwołania projektu</span><span class="sxs-lookup"><span data-stu-id="28796-269">Project references</span></span>

<span data-ttu-id="28796-270">Polecenie</span><span class="sxs-lookup"><span data-stu-id="28796-270">Command</span></span> | <span data-ttu-id="28796-271">Funkcja</span><span class="sxs-lookup"><span data-stu-id="28796-271">Function</span></span>
--- | ---
[<span data-ttu-id="28796-272">dotnet add reference</span><span class="sxs-lookup"><span data-stu-id="28796-272">dotnet add reference</span></span>](dotnet-add-reference.md) | <span data-ttu-id="28796-273">Dodaje odwołanie do projektu.</span><span class="sxs-lookup"><span data-stu-id="28796-273">Adds a project reference.</span></span>
[<span data-ttu-id="28796-274">dotnet list reference</span><span class="sxs-lookup"><span data-stu-id="28796-274">dotnet list reference</span></span>](dotnet-list-reference.md) | <span data-ttu-id="28796-275">Wyświetla listę odwołań do projektu.</span><span class="sxs-lookup"><span data-stu-id="28796-275">Lists project references.</span></span>
[<span data-ttu-id="28796-276">dotnet remove reference</span><span class="sxs-lookup"><span data-stu-id="28796-276">dotnet remove reference</span></span>](dotnet-remove-reference.md) | <span data-ttu-id="28796-277">Usuwa odwołanie do projektu.</span><span class="sxs-lookup"><span data-stu-id="28796-277">Removes a project reference.</span></span>

### <a name="nuget-packages"></a><span data-ttu-id="28796-278">Pakiety NuGet</span><span class="sxs-lookup"><span data-stu-id="28796-278">NuGet packages</span></span>

<span data-ttu-id="28796-279">Polecenie</span><span class="sxs-lookup"><span data-stu-id="28796-279">Command</span></span> | <span data-ttu-id="28796-280">Funkcja</span><span class="sxs-lookup"><span data-stu-id="28796-280">Function</span></span>
--- | ---
[<span data-ttu-id="28796-281">dotnet add package</span><span class="sxs-lookup"><span data-stu-id="28796-281">dotnet add package</span></span>](dotnet-add-package.md) | <span data-ttu-id="28796-282">Dodaje pakiet NuGet.</span><span class="sxs-lookup"><span data-stu-id="28796-282">Adds a NuGet package.</span></span>
[<span data-ttu-id="28796-283">dotnet remove package</span><span class="sxs-lookup"><span data-stu-id="28796-283">dotnet remove package</span></span>](dotnet-remove-package.md) | <span data-ttu-id="28796-284">Usuwa pakiet NuGet.</span><span class="sxs-lookup"><span data-stu-id="28796-284">Removes a NuGet package.</span></span>

### <a name="nuget-commands"></a><span data-ttu-id="28796-285">Polecenia NuGet</span><span class="sxs-lookup"><span data-stu-id="28796-285">NuGet commands</span></span>

<span data-ttu-id="28796-286">Polecenie</span><span class="sxs-lookup"><span data-stu-id="28796-286">Command</span></span> | <span data-ttu-id="28796-287">Funkcja</span><span class="sxs-lookup"><span data-stu-id="28796-287">Function</span></span>
--- | ---
[<span data-ttu-id="28796-288">dotnet nuget delete</span><span class="sxs-lookup"><span data-stu-id="28796-288">dotnet nuget delete</span></span>](dotnet-nuget-delete.md) | <span data-ttu-id="28796-289">Usuwa pakiet z serwera lub go wystawia.</span><span class="sxs-lookup"><span data-stu-id="28796-289">Deletes or unlists a package from the server.</span></span>
[<span data-ttu-id="28796-290">dotnet nuget locals</span><span class="sxs-lookup"><span data-stu-id="28796-290">dotnet nuget locals</span></span>](dotnet-nuget-locals.md) | <span data-ttu-id="28796-291">Czyści lub wyświetla lokalne zasoby NuGet, takie jak pamięć podręczna żądań HTTP, tymczasowa pamięć podręczna lub folder pakietów globalnych dla całego komputera.</span><span class="sxs-lookup"><span data-stu-id="28796-291">Clears or lists local NuGet resources such as http-request cache, temporary cache, or machine-wide global packages folder.</span></span>
[<span data-ttu-id="28796-292">dotnet nuget push</span><span class="sxs-lookup"><span data-stu-id="28796-292">dotnet nuget push</span></span>](dotnet-nuget-push.md) | <span data-ttu-id="28796-293">Wypchnij pakiet na serwer i opublikuje go.</span><span class="sxs-lookup"><span data-stu-id="28796-293">Pushes a package to the server and publishes it.</span></span>

### <a name="global-tools-commands"></a><span data-ttu-id="28796-294">Polecenia narzędzi globalnych</span><span class="sxs-lookup"><span data-stu-id="28796-294">Global Tools commands</span></span>

<span data-ttu-id="28796-295">[Narzędzia globalne platformy .NET Core](global-tools.md) są dostępne począwszy od zestaw .NET Core SDK 2.1.300:</span><span class="sxs-lookup"><span data-stu-id="28796-295">[.NET Core Global Tools](global-tools.md) are available starting with .NET Core SDK 2.1.300:</span></span>

<span data-ttu-id="28796-296">Polecenie</span><span class="sxs-lookup"><span data-stu-id="28796-296">Command</span></span> | <span data-ttu-id="28796-297">Funkcja</span><span class="sxs-lookup"><span data-stu-id="28796-297">Function</span></span>
--- | ---
[<span data-ttu-id="28796-298">dotnet tool install</span><span class="sxs-lookup"><span data-stu-id="28796-298">dotnet tool install</span></span>](dotnet-tool-install.md) | <span data-ttu-id="28796-299">Instaluje narzędzie globalne na komputerze.</span><span class="sxs-lookup"><span data-stu-id="28796-299">Installs a Global Tool on your machine.</span></span>
[<span data-ttu-id="28796-300">dotnet tool list</span><span class="sxs-lookup"><span data-stu-id="28796-300">dotnet tool list</span></span>](dotnet-tool-list.md) | <span data-ttu-id="28796-301">Wyświetla listę wszystkich narzędzi globalnych aktualnie zainstalowanych w domyślnym katalogu na komputerze lub w określonej ścieżce.</span><span class="sxs-lookup"><span data-stu-id="28796-301">Lists all Global Tools currently installed in the default directory on your machine or in the specified path.</span></span>
[<span data-ttu-id="28796-302">dotnet tool uninstall</span><span class="sxs-lookup"><span data-stu-id="28796-302">dotnet tool uninstall</span></span>](dotnet-tool-uninstall.md) | <span data-ttu-id="28796-303">Odinstalowuje narzędzie globalne z komputera.</span><span class="sxs-lookup"><span data-stu-id="28796-303">Uninstalls a Global Tool from your machine.</span></span>
[<span data-ttu-id="28796-304">dotnet tool update</span><span class="sxs-lookup"><span data-stu-id="28796-304">dotnet tool update</span></span>](dotnet-tool-update.md) | <span data-ttu-id="28796-305">Aktualizuje narzędzie globalne na komputerze.</span><span class="sxs-lookup"><span data-stu-id="28796-305">Updates a Global Tool on your machine.</span></span>

### <a name="additional-tools"></a><span data-ttu-id="28796-306">Dodatkowe narzędzia</span><span class="sxs-lookup"><span data-stu-id="28796-306">Additional tools</span></span>

<span data-ttu-id="28796-307">Począwszy od zestaw .NET Core SDK 2.1.300, wiele narzędzi, które były dostępne tylko dla każdego projektu, przy użyciu `DotnetCliToolReference` , jest teraz dostępne jako część zestaw .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="28796-307">Starting with .NET Core SDK 2.1.300, a number of tools that were available only on a per project basis using `DotnetCliToolReference` are now available as part of the .NET Core SDK.</span></span> <span data-ttu-id="28796-308">Te narzędzia są wymienione w poniższej tabeli:</span><span class="sxs-lookup"><span data-stu-id="28796-308">These tools are listed in the following table:</span></span>

| <span data-ttu-id="28796-309">Narzędzie</span><span class="sxs-lookup"><span data-stu-id="28796-309">Tool</span></span>                                              | <span data-ttu-id="28796-310">Funkcja</span><span class="sxs-lookup"><span data-stu-id="28796-310">Function</span></span>                                                     |
| ------------------------------------------------- | ------------------------------------------------------------ |
| <span data-ttu-id="28796-311">dev-certs</span><span class="sxs-lookup"><span data-stu-id="28796-311">dev-certs</span></span>                                         | <span data-ttu-id="28796-312">Tworzy i zarządza certyfikatami deweloperskimi.</span><span class="sxs-lookup"><span data-stu-id="28796-312">Creates and manages development certificates.</span></span>                |
| [<span data-ttu-id="28796-313">bieżąco</span><span class="sxs-lookup"><span data-stu-id="28796-313">ef</span></span>](/ef/core/miscellaneous/cli/dotnet)           | <span data-ttu-id="28796-314">Entity Framework Core narzędzia wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="28796-314">Entity Framework Core command-line tools.</span></span>                    |
| <span data-ttu-id="28796-315">SQL-pamięć podręczna</span><span class="sxs-lookup"><span data-stu-id="28796-315">sql-cache</span></span>                                         | <span data-ttu-id="28796-316">SQL Server narzędzia wiersza polecenia pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="28796-316">SQL Server cache command-line tools.</span></span>                         |
| [<span data-ttu-id="28796-317">wpisy tajne użytkownika</span><span class="sxs-lookup"><span data-stu-id="28796-317">user-secrets</span></span>](/aspnet/core/security/app-secrets) | <span data-ttu-id="28796-318">Zarządza kluczami tajnymi użytkowników deweloperskich.</span><span class="sxs-lookup"><span data-stu-id="28796-318">Manages development user secrets.</span></span>                            |
| [<span data-ttu-id="28796-319">Obejrzyj</span><span class="sxs-lookup"><span data-stu-id="28796-319">watch</span></span>](/aspnet/core/tutorials/dotnet-watch)      | <span data-ttu-id="28796-320">Uruchamia obserwatora plików, który uruchamia polecenie, gdy pliki zmienią się.</span><span class="sxs-lookup"><span data-stu-id="28796-320">Starts a file watcher that runs a command when files change.</span></span> |

<span data-ttu-id="28796-321">Aby uzyskać więcej informacji na temat każdego narzędzia `dotnet <tool-name> --help`, wpisz.</span><span class="sxs-lookup"><span data-stu-id="28796-321">For more information about each tool, type `dotnet <tool-name> --help`.</span></span>

## <a name="examples"></a><span data-ttu-id="28796-322">Przykłady</span><span class="sxs-lookup"><span data-stu-id="28796-322">Examples</span></span>

<span data-ttu-id="28796-323">Tworzy nową aplikację konsolową platformy .NET Core:</span><span class="sxs-lookup"><span data-stu-id="28796-323">Creates a new .NET Core console application:</span></span>

`dotnet new console`

<span data-ttu-id="28796-324">Przywróć zależności dla danej aplikacji:</span><span class="sxs-lookup"><span data-stu-id="28796-324">Restore dependencies for a given application:</span></span>

`dotnet restore`

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

<span data-ttu-id="28796-325">Kompiluj projekt i jego zależności w danym katalogu:</span><span class="sxs-lookup"><span data-stu-id="28796-325">Build a project and its dependencies in a given directory:</span></span>

`dotnet build`

<span data-ttu-id="28796-326">Uruchom bibliotekę DLL aplikacji, na `myapp.dll`przykład:</span><span class="sxs-lookup"><span data-stu-id="28796-326">Run an application DLL, such as `myapp.dll`:</span></span>

`dotnet myapp.dll`

## <a name="environment-variables"></a><span data-ttu-id="28796-327">Zmienne środowiskowe</span><span class="sxs-lookup"><span data-stu-id="28796-327">Environment variables</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="28796-328">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="28796-328">.NET Core 2.1</span></span>](#tab/netcore21)

`DOTNET_PACKAGES`

<span data-ttu-id="28796-329">Folder pakiety globalne.</span><span class="sxs-lookup"><span data-stu-id="28796-329">The global packages folder.</span></span> <span data-ttu-id="28796-330">Jeśli nie jest ustawiona, zostanie ona `~/.nuget/packages` domyślnie włączona w `%userprofile%\.nuget\packages` systemie UNIX lub w systemie Windows.</span><span class="sxs-lookup"><span data-stu-id="28796-330">If not set, it defaults to `~/.nuget/packages` on Unix or `%userprofile%\.nuget\packages` on Windows.</span></span>

`DOTNET_SERVICING`

<span data-ttu-id="28796-331">Określa lokalizację indeksu obsługi, który ma być używany przez host udostępniony podczas ładowania środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="28796-331">Specifies the location of the servicing index to use by the shared host when loading the runtime.</span></span>

`DOTNET_CLI_TELEMETRY_OPTOUT`

<span data-ttu-id="28796-332">Określa, czy dane dotyczące użycia narzędzi .NET Core są zbierane i wysyłane do firmy Microsoft.</span><span class="sxs-lookup"><span data-stu-id="28796-332">Specifies whether data about the .NET Core tools usage is collected and sent to Microsoft.</span></span> <span data-ttu-id="28796-333">Ustaw, `true` aby zrezygnować z funkcji telemetrii (wartości `true`, `1`lub `yes` zaakceptować).</span><span class="sxs-lookup"><span data-stu-id="28796-333">Set to `true` to opt-out of the telemetry feature (values `true`, `1`, or `yes` accepted).</span></span> <span data-ttu-id="28796-334">W przeciwnym razie ustaw `false` opcję, aby można było wybrać funkcje telemetrii ( `no` wartości `false`, `0`lub zaakceptowane).</span><span class="sxs-lookup"><span data-stu-id="28796-334">Otherwise, set to `false` to opt into the telemetry features (values `false`, `0`, or `no` accepted).</span></span> <span data-ttu-id="28796-335">Jeśli nie zostanie ustawiona, wartość domyślna `false` to i aktywna funkcja telemetrii.</span><span class="sxs-lookup"><span data-stu-id="28796-335">If not set, the default is `false` and the telemetry feature is active.</span></span>

`DOTNET_MULTILEVEL_LOOKUP`

<span data-ttu-id="28796-336">Określa, czy środowisko uruchomieniowe programu .NET Core, udostępnione środowisko lub zestaw SDK są rozpoznawane z lokalizacji globalnej.</span><span class="sxs-lookup"><span data-stu-id="28796-336">Specifies whether .NET Core runtime, shared framework, or SDK are resolved from the global location.</span></span> <span data-ttu-id="28796-337">Jeśli nie zostanie ustawiona, domyślnie `true`jest to.</span><span class="sxs-lookup"><span data-stu-id="28796-337">If not set, it defaults to `true`.</span></span> <span data-ttu-id="28796-338">Ustawiona na `false` wartość nie jest rozpoznawana z lokalizacji globalnej i ma wyizolowane instalacje .NET `0` Core `false` (wartości lub są akceptowane).</span><span class="sxs-lookup"><span data-stu-id="28796-338">Set to `false` to not resolve from the global location and have isolated .NET Core installations (values `0` or `false` are accepted).</span></span> <span data-ttu-id="28796-339">Aby uzyskać więcej informacji o wyszukiwaniu wielu poziomów, zobacz [SharedFX wyszukiwanie na wielu poziomach](https://github.com/dotnet/core-setup/blob/master/Documentation/design-docs/multilevel-sharedfx-lookup.md).</span><span class="sxs-lookup"><span data-stu-id="28796-339">For more information about multi-level lookup, see [Multi-level SharedFX Lookup](https://github.com/dotnet/core-setup/blob/master/Documentation/design-docs/multilevel-sharedfx-lookup.md).</span></span>

`DOTNET_ROLL_FORWARD_ON_NO_CANDIDATE_FX`

<span data-ttu-id="28796-340">Wyłącza dodatkową wersję do przodu, jeśli jest ustawiona `0`na.</span><span class="sxs-lookup"><span data-stu-id="28796-340">Disables minor version roll forward, if set to `0`.</span></span> <span data-ttu-id="28796-341">Aby uzyskać więcej informacji, zobacz [przewinięcie do przodu](../whats-new/dotnet-core-2-1.md#roll-forward).</span><span class="sxs-lookup"><span data-stu-id="28796-341">For more information, see [Roll forward](../whats-new/dotnet-core-2-1.md#roll-forward).</span></span>

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="28796-342">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="28796-342">.NET Core 2.0</span></span>](#tab/netcore20)

`DOTNET_PACKAGES`

<span data-ttu-id="28796-343">Podstawowa pamięć podręczna pakietu.</span><span class="sxs-lookup"><span data-stu-id="28796-343">The primary package cache.</span></span> <span data-ttu-id="28796-344">Jeśli nie jest ustawiona, zostanie ona `$HOME/.nuget/packages` domyślnie włączona w `%userprofile%\.nuget\packages` systemie UNIX lub w systemie Windows.</span><span class="sxs-lookup"><span data-stu-id="28796-344">If not set, it defaults to `$HOME/.nuget/packages` on Unix or `%userprofile%\.nuget\packages` on Windows.</span></span>

`DOTNET_SERVICING`

<span data-ttu-id="28796-345">Określa lokalizację indeksu obsługi, który ma być używany przez host udostępniony podczas ładowania środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="28796-345">Specifies the location of the servicing index to use by the shared host when loading the runtime.</span></span>

`DOTNET_CLI_TELEMETRY_OPTOUT`

<span data-ttu-id="28796-346">Określa, czy dane dotyczące użycia narzędzi .NET Core są zbierane i wysyłane do firmy Microsoft.</span><span class="sxs-lookup"><span data-stu-id="28796-346">Specifies whether data about the .NET Core tools usage is collected and sent to Microsoft.</span></span> <span data-ttu-id="28796-347">Ustaw, `true` aby zrezygnować z funkcji telemetrii (wartości `true`, `1`lub `yes` zaakceptować).</span><span class="sxs-lookup"><span data-stu-id="28796-347">Set to `true` to opt-out of the telemetry feature (values `true`, `1`, or `yes` accepted).</span></span> <span data-ttu-id="28796-348">W przeciwnym razie ustaw `false` opcję, aby można było wybrać funkcje telemetrii ( `no` wartości `false`, `0`lub zaakceptowane).</span><span class="sxs-lookup"><span data-stu-id="28796-348">Otherwise, set to `false` to opt into the telemetry features (values `false`, `0`, or `no` accepted).</span></span> <span data-ttu-id="28796-349">Jeśli nie zostanie ustawiona, wartość domyślna `false` to i aktywna funkcja telemetrii.</span><span class="sxs-lookup"><span data-stu-id="28796-349">If not set, the default is `false` and the telemetry feature is active.</span></span>

`DOTNET_MULTILEVEL_LOOKUP`

<span data-ttu-id="28796-350">Określa, czy środowisko uruchomieniowe programu .NET Core, udostępnione środowisko lub zestaw SDK są rozpoznawane z lokalizacji globalnej.</span><span class="sxs-lookup"><span data-stu-id="28796-350">Specifies whether .NET Core runtime, shared framework, or SDK are resolved from the global location.</span></span> <span data-ttu-id="28796-351">Jeśli nie zostanie ustawiona, domyślnie `true`jest to.</span><span class="sxs-lookup"><span data-stu-id="28796-351">If not set, it defaults to `true`.</span></span> <span data-ttu-id="28796-352">Ustawiona na `false` wartość nie jest rozpoznawana z lokalizacji globalnej i ma wyizolowane instalacje .NET `0` Core `false` (wartości lub są akceptowane).</span><span class="sxs-lookup"><span data-stu-id="28796-352">Set to `false` to not resolve from the global location and have isolated .NET Core installations (values `0` or `false` are accepted).</span></span> <span data-ttu-id="28796-353">Aby uzyskać więcej informacji o wyszukiwaniu wielu poziomów, zobacz [SharedFX wyszukiwanie na wielu poziomach](https://github.com/dotnet/core-setup/blob/master/Documentation/design-docs/multilevel-sharedfx-lookup.md).</span><span class="sxs-lookup"><span data-stu-id="28796-353">For more information about multi-level lookup, see [Multi-level SharedFX Lookup](https://github.com/dotnet/core-setup/blob/master/Documentation/design-docs/multilevel-sharedfx-lookup.md).</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="28796-354">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="28796-354">.NET Core 1.x</span></span>](#tab/netcore1x)

`DOTNET_PACKAGES`

<span data-ttu-id="28796-355">Podstawowa pamięć podręczna pakietu.</span><span class="sxs-lookup"><span data-stu-id="28796-355">The primary package cache.</span></span> <span data-ttu-id="28796-356">Jeśli nie jest ustawiona, zostanie ona `$HOME/.nuget/packages` domyślnie włączona w `%userprofile%\.nuget\packages` systemie UNIX lub w systemie Windows.</span><span class="sxs-lookup"><span data-stu-id="28796-356">If not set, it defaults to `$HOME/.nuget/packages` on Unix or `%userprofile%\.nuget\packages` on Windows.</span></span>

`DOTNET_SERVICING`

<span data-ttu-id="28796-357">Określa lokalizację indeksu obsługi, który ma być używany przez host udostępniony podczas ładowania środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="28796-357">Specifies the location of the servicing index to use by the shared host when loading the runtime.</span></span>

`DOTNET_CLI_TELEMETRY_OPTOUT`

<span data-ttu-id="28796-358">Określa, czy dane dotyczące użycia narzędzi .NET Core są zbierane i wysyłane do firmy Microsoft.</span><span class="sxs-lookup"><span data-stu-id="28796-358">Specifies whether data about the .NET Core tools usage is collected and sent to Microsoft.</span></span> <span data-ttu-id="28796-359">Ustaw, `true` aby zrezygnować z funkcji telemetrii (wartości `true`, `1`lub `yes` zaakceptować).</span><span class="sxs-lookup"><span data-stu-id="28796-359">Set to `true` to opt-out of the telemetry feature (values `true`, `1`, or `yes` accepted).</span></span> <span data-ttu-id="28796-360">W przeciwnym razie ustaw `false` opcję, aby można było wybrać funkcje telemetrii ( `no` wartości `false`, `0`lub zaakceptowane).</span><span class="sxs-lookup"><span data-stu-id="28796-360">Otherwise, set to `false` to opt into the telemetry features (values `false`, `0`, or `no` accepted).</span></span> <span data-ttu-id="28796-361">Jeśli nie zostanie ustawiona, wartość domyślna `false` to i aktywna funkcja telemetrii.</span><span class="sxs-lookup"><span data-stu-id="28796-361">If not set, the default is `false` and the telemetry feature is active.</span></span>

---

## <a name="see-also"></a><span data-ttu-id="28796-362">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="28796-362">See also</span></span>

- [<span data-ttu-id="28796-363">Pliki konfiguracji środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="28796-363">Runtime Configuration Files</span></span>](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md)
