---
title: dotnet — polecenie
description: Dowiedz się więcej na temat polecenia dotnet (sterownika generycznego dla narzędzi interfejs wiersza polecenia platformy .NET Core) i jego użycia.
ms.date: 06/04/2018
ms.openlocfilehash: fe90968560b58471c279fcd2097741ea476cef0b
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76734069"
---
# <a name="dotnet-command"></a><span data-ttu-id="bfb56-103">dotnet — polecenie</span><span class="sxs-lookup"><span data-stu-id="bfb56-103">dotnet command</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="bfb56-104">Nazwa</span><span class="sxs-lookup"><span data-stu-id="bfb56-104">Name</span></span>

<span data-ttu-id="bfb56-105">`dotnet` — narzędzie do zarządzania kodem źródłowym i plikami binarnymi platformy .NET.</span><span class="sxs-lookup"><span data-stu-id="bfb56-105">`dotnet` - A tool for managing .NET source code and binaries.</span></span>

## <a name="synopsis"></a><span data-ttu-id="bfb56-106">Streszczenie</span><span class="sxs-lookup"><span data-stu-id="bfb56-106">Synopsis</span></span>

<!-- markdownlint-disable MD025 -->

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="bfb56-107">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="bfb56-107">.NET Core 2.1</span></span>](#tab/netcore21)

```dotnetcli
dotnet [command] [arguments] [--additional-deps] [--additionalprobingpath] [--depsfile]
    [-d|--diagnostics] [--fx-version] [-h|--help] [--info] [--list-runtimes] [--list-sdks] [--roll-forward-on-no-candidate-fx] [--runtimeconfig] [-v|--verbosity] [--version]
```

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="bfb56-108">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="bfb56-108">.NET Core 2.0</span></span>](#tab/netcore20)

```dotnetcli
dotnet [command] [arguments] [--additional-deps] [--additionalprobingpath] [--depsfile]
    [-d|--diagnostics] [--fx-version] [-h|--help] [--info] [--roll-forward-on-no-candidate-fx]
    [--runtimeconfig] [-v|--verbosity] [--version]
```

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="bfb56-109">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="bfb56-109">.NET Core 1.x</span></span>](#tab/netcore1x)

```dotnetcli
dotnet [command] [arguments] [--additionalprobingpath] [--depsfile] [-d|--diagnostics]
    [--fx-version] [-h|--help] [--info] [--runtimeconfig] [-v|--verbosity] [--version]
```

---

## <a name="description"></a><span data-ttu-id="bfb56-110">Opis</span><span class="sxs-lookup"><span data-stu-id="bfb56-110">Description</span></span>

<span data-ttu-id="bfb56-111">`dotnet` jest narzędziem do zarządzania kodem źródłowym i plikami binarnymi programu .NET.</span><span class="sxs-lookup"><span data-stu-id="bfb56-111">`dotnet` is a tool for managing .NET source code and binaries.</span></span> <span data-ttu-id="bfb56-112">Udostępnia polecenia wykonujące określone zadania, takie jak [`dotnet build`](dotnet-build.md) i [`dotnet run`](dotnet-run.md).</span><span class="sxs-lookup"><span data-stu-id="bfb56-112">It exposes commands that perform specific tasks, such as [`dotnet build`](dotnet-build.md) and [`dotnet run`](dotnet-run.md).</span></span> <span data-ttu-id="bfb56-113">Każde polecenie definiuje własne argumenty.</span><span class="sxs-lookup"><span data-stu-id="bfb56-113">Each command defines its own arguments.</span></span> <span data-ttu-id="bfb56-114">Wpisz `--help` po każdym poleceniu, aby uzyskać dostęp do krótkiej dokumentacji pomocy.</span><span class="sxs-lookup"><span data-stu-id="bfb56-114">Type `--help` after each command to access brief help documentation.</span></span>

<span data-ttu-id="bfb56-115">`dotnet` można używać do uruchamiania aplikacji przez określenie biblioteki DLL aplikacji, takiej jak `dotnet myapp.dll`.</span><span class="sxs-lookup"><span data-stu-id="bfb56-115">`dotnet` can be used to run applications, by specifying an application DLL, such as `dotnet myapp.dll`.</span></span> <span data-ttu-id="bfb56-116">Zobacz [wdrażanie aplikacji .NET Core](../deploying/index.md) w celu uzyskania informacji na temat opcji wdrażania.</span><span class="sxs-lookup"><span data-stu-id="bfb56-116">See [.NET Core application deployment](../deploying/index.md) for to learn about deployment options.</span></span>

## <a name="options"></a><span data-ttu-id="bfb56-117">Opcje</span><span class="sxs-lookup"><span data-stu-id="bfb56-117">Options</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="bfb56-118">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="bfb56-118">.NET Core 2.1</span></span>](#tab/netcore21)

`--additional-deps <PATH>`

<span data-ttu-id="bfb56-119">Ścieżka do dodatkowego pliku *. deps. JSON* .</span><span class="sxs-lookup"><span data-stu-id="bfb56-119">Path to an additional *.deps.json* file.</span></span>

`--additionalprobingpath <PATH>`

<span data-ttu-id="bfb56-120">Ścieżka zawierająca zasady i zestawy do sondowania.</span><span class="sxs-lookup"><span data-stu-id="bfb56-120">Path containing probing policy and assemblies to probe.</span></span>

`--depsfile`

<span data-ttu-id="bfb56-121">Ścieżka do pliku *deps. JSON* .</span><span class="sxs-lookup"><span data-stu-id="bfb56-121">Path to a *deps.json* file.</span></span>

<span data-ttu-id="bfb56-122">Plik *deps. JSON* zawiera listę zależności, zależności kompilacji i informacje o wersji używane do rozwiązywania konfliktów zestawów.</span><span class="sxs-lookup"><span data-stu-id="bfb56-122">A *deps.json* file contains a list of dependencies, compilation dependencies, and version information used to address assembly conflicts.</span></span> <span data-ttu-id="bfb56-123">Aby uzyskać więcej informacji na temat tego pliku, zobacz [pliki konfiguracji środowiska uruchomieniowego](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md) w serwisie GitHub.</span><span class="sxs-lookup"><span data-stu-id="bfb56-123">For more information about this file, see [Runtime Configuration Files](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md) on GitHub.</span></span>

`-d|--diagnostics`

<span data-ttu-id="bfb56-124">Włącza diagnostykę danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="bfb56-124">Enables diagnostic output.</span></span>

`--fx-version <VERSION>`

<span data-ttu-id="bfb56-125">Wersja środowiska uruchomieniowego platformy .NET Core do użycia w celu uruchomienia aplikacji.</span><span class="sxs-lookup"><span data-stu-id="bfb56-125">Version of the .NET Core runtime to use to run the application.</span></span>

`-h|--help`

<span data-ttu-id="bfb56-126">Drukuje dokumentację dla danego polecenia, taką jak `dotnet build --help`.</span><span class="sxs-lookup"><span data-stu-id="bfb56-126">Prints out documentation for a given command, such as `dotnet build --help`.</span></span> <span data-ttu-id="bfb56-127">`dotnet --help` drukuje listę dostępnych poleceń.</span><span class="sxs-lookup"><span data-stu-id="bfb56-127">`dotnet --help` prints a list of available commands.</span></span>

`--info`

<span data-ttu-id="bfb56-128">Drukuje szczegółowe informacje na temat instalacji programu .NET Core i środowiska maszynowego, takiego jak bieżący system operacyjny, i zatwierdzania SHA dla wersji .NET Core.</span><span class="sxs-lookup"><span data-stu-id="bfb56-128">Prints out detailed information about a .NET Core installation and the machine environment, such as the current operating system, and commit SHA of the .NET Core version.</span></span>

`--list-runtimes`

<span data-ttu-id="bfb56-129">Wyświetla zainstalowane środowiska uruchomieniowe platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="bfb56-129">Displays the installed .NET Core runtimes.</span></span>

`--list-sdks`

<span data-ttu-id="bfb56-130">Wyświetla zainstalowane zestawy SDK platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="bfb56-130">Displays the installed .NET Core SDKs.</span></span>

`--roll-forward-on-no-candidate-fx <N>`

<span data-ttu-id="bfb56-131">Definiuje zachowanie, gdy wymagana architektura udostępniona jest niedostępna.</span><span class="sxs-lookup"><span data-stu-id="bfb56-131">Defines behavior when the required shared framework is not available.</span></span> <span data-ttu-id="bfb56-132">`N` może być:</span><span class="sxs-lookup"><span data-stu-id="bfb56-132">`N` can be:</span></span>

- <span data-ttu-id="bfb56-133">`0` — Wyłącz nawet dodatkową wersję pomocniczą.</span><span class="sxs-lookup"><span data-stu-id="bfb56-133">`0` - Disable even minor version roll forward.</span></span>
- <span data-ttu-id="bfb56-134">`1` — przewinięcie do wersji pomocniczej, ale nie w wersji głównej.</span><span class="sxs-lookup"><span data-stu-id="bfb56-134">`1` - Roll forward on minor version, but not on major version.</span></span> <span data-ttu-id="bfb56-135">Jest to zachowanie domyślne.</span><span class="sxs-lookup"><span data-stu-id="bfb56-135">This is the default behavior.</span></span>
- <span data-ttu-id="bfb56-136">`2` — przewinięcie w przód do wersji pomocniczych i głównych.</span><span class="sxs-lookup"><span data-stu-id="bfb56-136">`2` - Roll forward on minor and major versions.</span></span>

 <span data-ttu-id="bfb56-137">Aby uzyskać więcej informacji, zobacz [przewinięcie do przodu](../whats-new/dotnet-core-2-1.md#roll-forward).</span><span class="sxs-lookup"><span data-stu-id="bfb56-137">For more information, see [Roll forward](../whats-new/dotnet-core-2-1.md#roll-forward).</span></span>

`--runtimeconfig`

<span data-ttu-id="bfb56-138">Ścieżka do pliku *runtimeconfig. JSON* .</span><span class="sxs-lookup"><span data-stu-id="bfb56-138">Path to a *runtimeconfig.json* file.</span></span>

<span data-ttu-id="bfb56-139">Plik *runtimeconfig. JSON* to plik konfiguracji zawierający ustawienia czasu wykonywania.</span><span class="sxs-lookup"><span data-stu-id="bfb56-139">A *runtimeconfig.json* file is a configuration file containing run-time settings.</span></span> <span data-ttu-id="bfb56-140">Aby uzyskać więcej informacji, zobacz [Ustawienia konfiguracji środowiska uruchomieniowego .NET Core](../run-time-config/index.md#runtimeconfigjson).</span><span class="sxs-lookup"><span data-stu-id="bfb56-140">For more information, see [.NET Core run-time configuration settings](../run-time-config/index.md#runtimeconfigjson).</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="bfb56-141">Ustawia poziom szczegółowości polecenia.</span><span class="sxs-lookup"><span data-stu-id="bfb56-141">Sets the verbosity level of the command.</span></span> <span data-ttu-id="bfb56-142">Dozwolone wartości to `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`i `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="bfb56-142">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="bfb56-143">Nieobsługiwane w każdym poleceniu; Aby określić, czy ta opcja jest dostępna, zobacz określoną stronę poleceń.</span><span class="sxs-lookup"><span data-stu-id="bfb56-143">Not supported in every command; see specific command page to determine if this option is available.</span></span>

`--version`

<span data-ttu-id="bfb56-144">Drukuje używaną wersję zestaw .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="bfb56-144">Prints out the version of the .NET Core SDK in use.</span></span>

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="bfb56-145">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="bfb56-145">.NET Core 2.0</span></span>](#tab/netcore20)

`--additional-deps <PATH>`

<span data-ttu-id="bfb56-146">Ścieżka do dodatkowego pliku *. deps. JSON* .</span><span class="sxs-lookup"><span data-stu-id="bfb56-146">Path to an additional *.deps.json* file.</span></span>

`--additionalprobingpath <PATH>`

<span data-ttu-id="bfb56-147">Ścieżka zawierająca zasady i zestawy do sondowania.</span><span class="sxs-lookup"><span data-stu-id="bfb56-147">Path containing probing policy and assemblies to probe.</span></span>

`--depsfile`

<span data-ttu-id="bfb56-148">Ścieżka do pliku *deps. JSON* .</span><span class="sxs-lookup"><span data-stu-id="bfb56-148">Path to a *deps.json* file.</span></span>

<span data-ttu-id="bfb56-149">Plik *deps. JSON* zawiera listę zależności, zależności kompilacji i informacje o wersji używane do rozwiązywania konfliktów zestawów.</span><span class="sxs-lookup"><span data-stu-id="bfb56-149">A *deps.json* file contains a list of dependencies, compilation dependencies and version information used to address assembly conflicts.</span></span> <span data-ttu-id="bfb56-150">Aby uzyskać więcej informacji na temat tego pliku, zobacz [pliki konfiguracji środowiska uruchomieniowego w serwisie GitHub](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md).</span><span class="sxs-lookup"><span data-stu-id="bfb56-150">For more details on this file, see [Runtime Configuration Files on GitHub](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md).</span></span>

`-d|--diagnostics`

<span data-ttu-id="bfb56-151">Włącza diagnostykę danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="bfb56-151">Enables diagnostic output.</span></span>

`--fx-version <VERSION>`

<span data-ttu-id="bfb56-152">Wersja środowiska uruchomieniowego platformy .NET Core do użycia w celu uruchomienia aplikacji.</span><span class="sxs-lookup"><span data-stu-id="bfb56-152">Version of the .NET Core runtime to use to run the application.</span></span>

`-h|--help`

<span data-ttu-id="bfb56-153">Drukuje dokumentację dla danego polecenia, taką jak `dotnet build --help`.</span><span class="sxs-lookup"><span data-stu-id="bfb56-153">Prints out documentation for a given command, such as `dotnet build --help`.</span></span> <span data-ttu-id="bfb56-154">`dotnet --help` drukuje listę dostępnych poleceń.</span><span class="sxs-lookup"><span data-stu-id="bfb56-154">`dotnet --help` prints a list of available commands.</span></span>

`--info`

<span data-ttu-id="bfb56-155">Drukuje szczegółowe informacje na temat instalacji programu .NET Core i środowiska maszynowego, takiego jak bieżący system operacyjny, i zatwierdzania SHA dla wersji .NET Core.</span><span class="sxs-lookup"><span data-stu-id="bfb56-155">Prints out detailed information about a .NET Core installation and the machine environment, such as the current operating system, and commit SHA of the .NET Core version.</span></span>

`--roll-forward-on-no-candidate-fx`

 <span data-ttu-id="bfb56-156">Wyłącza opcję wycofywania wersji pomocniczej, jeśli jest ustawiona na `0`.</span><span class="sxs-lookup"><span data-stu-id="bfb56-156">Disables minor version roll forward, if set to `0`.</span></span> <span data-ttu-id="bfb56-157">Aby uzyskać więcej informacji, zobacz [przewinięcie do przodu](../whats-new/dotnet-core-2-1.md#roll-forward).</span><span class="sxs-lookup"><span data-stu-id="bfb56-157">For more information, see [Roll forward](../whats-new/dotnet-core-2-1.md#roll-forward).</span></span>

`--runtimeconfig`

<span data-ttu-id="bfb56-158">Ścieżka do pliku *runtimeconfig. JSON* .</span><span class="sxs-lookup"><span data-stu-id="bfb56-158">Path to a *runtimeconfig.json* file.</span></span>

<span data-ttu-id="bfb56-159">Plik *runtimeconfig. JSON* to plik konfiguracji zawierający ustawienia czasu wykonywania.</span><span class="sxs-lookup"><span data-stu-id="bfb56-159">A *runtimeconfig.json* file is a configuration file containing run-time settings.</span></span> <span data-ttu-id="bfb56-160">Aby uzyskać więcej informacji, zobacz [Ustawienia konfiguracji środowiska uruchomieniowego .NET Core](../run-time-config/index.md#runtimeconfigjson).</span><span class="sxs-lookup"><span data-stu-id="bfb56-160">For more information, see [.NET Core run-time configuration settings](../run-time-config/index.md#runtimeconfigjson).</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="bfb56-161">Ustawia poziom szczegółowości polecenia.</span><span class="sxs-lookup"><span data-stu-id="bfb56-161">Sets the verbosity level of the command.</span></span> <span data-ttu-id="bfb56-162">Dozwolone wartości to `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`i `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="bfb56-162">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="bfb56-163">Nieobsługiwane w każdym poleceniu; Aby określić, czy ta opcja jest dostępna, zobacz określoną stronę poleceń.</span><span class="sxs-lookup"><span data-stu-id="bfb56-163">Not supported in every command; see specific command page to determine if this option is available.</span></span>

`--version`

<span data-ttu-id="bfb56-164">Drukuje używaną wersję zestaw .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="bfb56-164">Prints out the version of the .NET Core SDK in use.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="bfb56-165">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="bfb56-165">.NET Core 1.x</span></span>](#tab/netcore1x)

`--additionalprobingpath <PATH>`

<span data-ttu-id="bfb56-166">Ścieżka zawierająca zasady i zestawy do sondowania.</span><span class="sxs-lookup"><span data-stu-id="bfb56-166">Path containing probing policy and assemblies to probe.</span></span>

`--depsfile`

<span data-ttu-id="bfb56-167">Ścieżka do pliku *deps. JSON* .</span><span class="sxs-lookup"><span data-stu-id="bfb56-167">Path to a *deps.json* file.</span></span>

<span data-ttu-id="bfb56-168">Plik *deps. JSON* zawiera listę zależności, zależności kompilacji i informacje o wersji używane do rozwiązywania konfliktów zestawów.</span><span class="sxs-lookup"><span data-stu-id="bfb56-168">A *deps.json* file contains a list of dependencies, compilation dependencies and version information used to address assembly conflicts.</span></span> <span data-ttu-id="bfb56-169">Aby uzyskać więcej informacji na temat tego pliku, zobacz [pliki konfiguracji środowiska uruchomieniowego w serwisie GitHub](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md).</span><span class="sxs-lookup"><span data-stu-id="bfb56-169">For more details on this file, see [Runtime Configuration Files on GitHub](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md).</span></span>

`-d|--diagnostics`

<span data-ttu-id="bfb56-170">Włącza diagnostykę danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="bfb56-170">Enables diagnostic output.</span></span>

`--fx-version <VERSION>`

<span data-ttu-id="bfb56-171">Wersja środowiska uruchomieniowego platformy .NET Core do użycia w celu uruchomienia aplikacji.</span><span class="sxs-lookup"><span data-stu-id="bfb56-171">Version of the .NET Core runtime to use to run the application.</span></span>

`-h|--help`

<span data-ttu-id="bfb56-172">Drukuje dokumentację dla danego polecenia, taką jak `dotnet build --help`.</span><span class="sxs-lookup"><span data-stu-id="bfb56-172">Prints out documentation for a given command, such as `dotnet build --help`.</span></span> <span data-ttu-id="bfb56-173">`dotnet --help` drukuje listę dostępnych poleceń.</span><span class="sxs-lookup"><span data-stu-id="bfb56-173">`dotnet --help` prints a list of available commands.</span></span>

`--info`

<span data-ttu-id="bfb56-174">Drukuje szczegółowe informacje na temat instalacji programu .NET Core i środowiska maszynowego, takiego jak bieżący system operacyjny, i zatwierdzania SHA dla wersji .NET Core.</span><span class="sxs-lookup"><span data-stu-id="bfb56-174">Prints out detailed information about a .NET Core installation and the machine environment, such as the current operating system, and commit SHA of the .NET Core version.</span></span>

`--runtimeconfig`

<span data-ttu-id="bfb56-175">Ścieżka do pliku *runtimeconfig. JSON* .</span><span class="sxs-lookup"><span data-stu-id="bfb56-175">Path to a *runtimeconfig.json* file.</span></span>

<span data-ttu-id="bfb56-176">Plik *runtimeconfig. JSON* to plik konfiguracji zawierający ustawienia czasu wykonywania.</span><span class="sxs-lookup"><span data-stu-id="bfb56-176">A *runtimeconfig.json* file is a configuration file containing run-time settings.</span></span> <span data-ttu-id="bfb56-177">Aby uzyskać więcej informacji, zobacz [Ustawienia konfiguracji środowiska uruchomieniowego .NET Core](../run-time-config/index.md#runtimeconfigjson).</span><span class="sxs-lookup"><span data-stu-id="bfb56-177">For more information, see [.NET Core run-time configuration settings](../run-time-config/index.md#runtimeconfigjson).</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="bfb56-178">Ustawia poziom szczegółowości polecenia.</span><span class="sxs-lookup"><span data-stu-id="bfb56-178">Sets the verbosity level of the command.</span></span> <span data-ttu-id="bfb56-179">Dozwolone wartości to `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`i `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="bfb56-179">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="bfb56-180">Nieobsługiwane w każdym poleceniu; Aby określić, czy ta opcja jest dostępna, zobacz określoną stronę poleceń.</span><span class="sxs-lookup"><span data-stu-id="bfb56-180">Not supported in every command; see specific command page to determine if this option is available.</span></span>

`--version`

<span data-ttu-id="bfb56-181">Drukuje używaną wersję zestaw .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="bfb56-181">Prints out the version of the .NET Core SDK in use.</span></span>

---

## <a name="dotnet-commands"></a><span data-ttu-id="bfb56-182">Polecenia dotnet</span><span class="sxs-lookup"><span data-stu-id="bfb56-182">dotnet commands</span></span>

### <a name="general"></a><span data-ttu-id="bfb56-183">Ogólne</span><span class="sxs-lookup"><span data-stu-id="bfb56-183">General</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="bfb56-184">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="bfb56-184">.NET Core 2.1</span></span>](#tab/netcore21)

| <span data-ttu-id="bfb56-185">Polecenie</span><span class="sxs-lookup"><span data-stu-id="bfb56-185">Command</span></span>                                       | <span data-ttu-id="bfb56-186">Funkcja</span><span class="sxs-lookup"><span data-stu-id="bfb56-186">Function</span></span>                                                            |
| --------------------------------------------- | ------------------------------------------------------------------- |
| [<span data-ttu-id="bfb56-187">dotnet build</span><span class="sxs-lookup"><span data-stu-id="bfb56-187">dotnet build</span></span>](dotnet-build.md)               | <span data-ttu-id="bfb56-188">Kompiluje aplikację platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="bfb56-188">Builds a .NET Core application.</span></span>                                     |
| [<span data-ttu-id="bfb56-189">dotnet build-server</span><span class="sxs-lookup"><span data-stu-id="bfb56-189">dotnet build-server</span></span>](dotnet-build-server.md) | <span data-ttu-id="bfb56-190">Współdziała z serwerami uruchomionymi przez kompilację.</span><span class="sxs-lookup"><span data-stu-id="bfb56-190">Interacts with servers started by a build.</span></span>                          |
| [<span data-ttu-id="bfb56-191">dotnet clean</span><span class="sxs-lookup"><span data-stu-id="bfb56-191">dotnet clean</span></span>](dotnet-clean.md)               | <span data-ttu-id="bfb56-192">Czyste dane wyjściowe kompilacji.</span><span class="sxs-lookup"><span data-stu-id="bfb56-192">Clean build outputs.</span></span>                                                |
| [<span data-ttu-id="bfb56-193">dotnet help</span><span class="sxs-lookup"><span data-stu-id="bfb56-193">dotnet help</span></span>](dotnet-help.md)                 | <span data-ttu-id="bfb56-194">Przedstawia bardziej szczegółową dokumentację dla polecenia w trybie online.</span><span class="sxs-lookup"><span data-stu-id="bfb56-194">Shows more detailed documentation online for the command.</span></span>           |
| [<span data-ttu-id="bfb56-195">dotnet migrate</span><span class="sxs-lookup"><span data-stu-id="bfb56-195">dotnet migrate</span></span>](dotnet-migrate.md)           | <span data-ttu-id="bfb56-196">Migruje prawidłowy projekt w wersji zapoznawczej 2 do projektu zestaw .NET Core SDK 1,0.</span><span class="sxs-lookup"><span data-stu-id="bfb56-196">Migrates a valid Preview 2 project to a .NET Core SDK 1.0 project.</span></span>  |
| [<span data-ttu-id="bfb56-197">dotnet msbuild</span><span class="sxs-lookup"><span data-stu-id="bfb56-197">dotnet msbuild</span></span>](dotnet-msbuild.md)           | <span data-ttu-id="bfb56-198">Zapewnia dostęp do wiersza polecenia programu MSBuild.</span><span class="sxs-lookup"><span data-stu-id="bfb56-198">Provides access to the MSBuild command line.</span></span>                        |
| [<span data-ttu-id="bfb56-199">dotnet new</span><span class="sxs-lookup"><span data-stu-id="bfb56-199">dotnet new</span></span>](dotnet-new.md)                   | <span data-ttu-id="bfb56-200">Inicjuje projekt C# lub F# dla danego szablonu.</span><span class="sxs-lookup"><span data-stu-id="bfb56-200">Initializes a C# or F# project for a given template.</span></span>                |
| [<span data-ttu-id="bfb56-201">dotnet pack</span><span class="sxs-lookup"><span data-stu-id="bfb56-201">dotnet pack</span></span>](dotnet-pack.md)                 | <span data-ttu-id="bfb56-202">Tworzy pakiet NuGet kodu.</span><span class="sxs-lookup"><span data-stu-id="bfb56-202">Creates a NuGet package of your code.</span></span>                               |
| [<span data-ttu-id="bfb56-203">dotnet publish</span><span class="sxs-lookup"><span data-stu-id="bfb56-203">dotnet publish</span></span>](dotnet-publish.md)           | <span data-ttu-id="bfb56-204">Publikuje zależne od programu .NET Framework lub samodzielną aplikację.</span><span class="sxs-lookup"><span data-stu-id="bfb56-204">Publishes a .NET framework-dependent or self-contained application.</span></span> |
| [<span data-ttu-id="bfb56-205">dotnet restore</span><span class="sxs-lookup"><span data-stu-id="bfb56-205">dotnet restore</span></span>](dotnet-restore.md)           | <span data-ttu-id="bfb56-206">Przywraca zależności dla danej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="bfb56-206">Restores the dependencies for a given application.</span></span>                  |
| [<span data-ttu-id="bfb56-207">dotnet run</span><span class="sxs-lookup"><span data-stu-id="bfb56-207">dotnet run</span></span>](dotnet-run.md)                   | <span data-ttu-id="bfb56-208">Uruchamia aplikację ze źródła.</span><span class="sxs-lookup"><span data-stu-id="bfb56-208">Runs the application from source.</span></span>                                   |
| [<span data-ttu-id="bfb56-209">dotnet sln</span><span class="sxs-lookup"><span data-stu-id="bfb56-209">dotnet sln</span></span>](dotnet-sln.md)                   | <span data-ttu-id="bfb56-210">Opcje dodawania, usuwania i wyświetlania listy projektów w pliku rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="bfb56-210">Options to add, remove, and list projects in a solution file.</span></span>       |
| [<span data-ttu-id="bfb56-211">dotnet store</span><span class="sxs-lookup"><span data-stu-id="bfb56-211">dotnet store</span></span>](dotnet-store.md)               | <span data-ttu-id="bfb56-212">Przechowuje zestawy w magazynie pakietów środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="bfb56-212">Stores assemblies in the runtime package store.</span></span>                     |
| [<span data-ttu-id="bfb56-213">dotnet test</span><span class="sxs-lookup"><span data-stu-id="bfb56-213">dotnet test</span></span>](dotnet-test.md)                 | <span data-ttu-id="bfb56-214">Uruchamia testy przy użyciu modułu uruchamiającego testy.</span><span class="sxs-lookup"><span data-stu-id="bfb56-214">Runs tests using a test runner.</span></span>                                     |

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="bfb56-215">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="bfb56-215">.NET Core 2.0</span></span>](#tab/netcore20)

| <span data-ttu-id="bfb56-216">Polecenie</span><span class="sxs-lookup"><span data-stu-id="bfb56-216">Command</span></span>                             | <span data-ttu-id="bfb56-217">Funkcja</span><span class="sxs-lookup"><span data-stu-id="bfb56-217">Function</span></span>                                                            |
| ----------------------------------- | ------------------------------------------------------------------- |
| [<span data-ttu-id="bfb56-218">dotnet build</span><span class="sxs-lookup"><span data-stu-id="bfb56-218">dotnet build</span></span>](dotnet-build.md)     | <span data-ttu-id="bfb56-219">Kompiluje aplikację platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="bfb56-219">Builds a .NET Core application.</span></span>                                     |
| [<span data-ttu-id="bfb56-220">dotnet clean</span><span class="sxs-lookup"><span data-stu-id="bfb56-220">dotnet clean</span></span>](dotnet-clean.md)     | <span data-ttu-id="bfb56-221">Czyste dane wyjściowe kompilacji.</span><span class="sxs-lookup"><span data-stu-id="bfb56-221">Clean build outputs.</span></span>                                              |
| [<span data-ttu-id="bfb56-222">dotnet help</span><span class="sxs-lookup"><span data-stu-id="bfb56-222">dotnet help</span></span>](dotnet-help.md)       | <span data-ttu-id="bfb56-223">Przedstawia bardziej szczegółową dokumentację dla polecenia w trybie online.</span><span class="sxs-lookup"><span data-stu-id="bfb56-223">Shows more detailed documentation online for the command.</span></span>           |
| [<span data-ttu-id="bfb56-224">dotnet migrate</span><span class="sxs-lookup"><span data-stu-id="bfb56-224">dotnet migrate</span></span>](dotnet-migrate.md) | <span data-ttu-id="bfb56-225">Migruje prawidłowy projekt w wersji zapoznawczej 2 do projektu zestaw .NET Core SDK 1,0.</span><span class="sxs-lookup"><span data-stu-id="bfb56-225">Migrates a valid Preview 2 project to a .NET Core SDK 1.0 project.</span></span>  |
| [<span data-ttu-id="bfb56-226">dotnet msbuild</span><span class="sxs-lookup"><span data-stu-id="bfb56-226">dotnet msbuild</span></span>](dotnet-msbuild.md) | <span data-ttu-id="bfb56-227">Zapewnia dostęp do wiersza polecenia programu MSBuild.</span><span class="sxs-lookup"><span data-stu-id="bfb56-227">Provides access to the MSBuild command line.</span></span>                        |
| [<span data-ttu-id="bfb56-228">dotnet new</span><span class="sxs-lookup"><span data-stu-id="bfb56-228">dotnet new</span></span>](dotnet-new.md)         | <span data-ttu-id="bfb56-229">Inicjuje projekt C# lub F# dla danego szablonu.</span><span class="sxs-lookup"><span data-stu-id="bfb56-229">Initializes a C# or F# project for a given template.</span></span>                |
| [<span data-ttu-id="bfb56-230">dotnet pack</span><span class="sxs-lookup"><span data-stu-id="bfb56-230">dotnet pack</span></span>](dotnet-pack.md)       | <span data-ttu-id="bfb56-231">Tworzy pakiet NuGet kodu.</span><span class="sxs-lookup"><span data-stu-id="bfb56-231">Creates a NuGet package of your code.</span></span>                               |
| [<span data-ttu-id="bfb56-232">dotnet publish</span><span class="sxs-lookup"><span data-stu-id="bfb56-232">dotnet publish</span></span>](dotnet-publish.md) | <span data-ttu-id="bfb56-233">Publikuje zależne od programu .NET Framework lub samodzielną aplikację.</span><span class="sxs-lookup"><span data-stu-id="bfb56-233">Publishes a .NET framework-dependent or self-contained application.</span></span> |
| [<span data-ttu-id="bfb56-234">dotnet restore</span><span class="sxs-lookup"><span data-stu-id="bfb56-234">dotnet restore</span></span>](dotnet-restore.md) | <span data-ttu-id="bfb56-235">Przywraca zależności dla danej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="bfb56-235">Restores the dependencies for a given application.</span></span>                  |
| [<span data-ttu-id="bfb56-236">dotnet run</span><span class="sxs-lookup"><span data-stu-id="bfb56-236">dotnet run</span></span>](dotnet-run.md)         | <span data-ttu-id="bfb56-237">Uruchamia aplikację ze źródła.</span><span class="sxs-lookup"><span data-stu-id="bfb56-237">Runs the application from source.</span></span>                                   |
| [<span data-ttu-id="bfb56-238">dotnet sln</span><span class="sxs-lookup"><span data-stu-id="bfb56-238">dotnet sln</span></span>](dotnet-sln.md)         | <span data-ttu-id="bfb56-239">Opcje dodawania, usuwania i wyświetlania listy projektów w pliku rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="bfb56-239">Options to add, remove, and list projects in a solution file.</span></span>       |
| [<span data-ttu-id="bfb56-240">dotnet store</span><span class="sxs-lookup"><span data-stu-id="bfb56-240">dotnet store</span></span>](dotnet-store.md)     | <span data-ttu-id="bfb56-241">Przechowuje zestawy w magazynie pakietów środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="bfb56-241">Stores assemblies in the runtime package store.</span></span>                     |
| [<span data-ttu-id="bfb56-242">dotnet test</span><span class="sxs-lookup"><span data-stu-id="bfb56-242">dotnet test</span></span>](dotnet-test.md)       | <span data-ttu-id="bfb56-243">Uruchamia testy przy użyciu modułu uruchamiającego testy.</span><span class="sxs-lookup"><span data-stu-id="bfb56-243">Runs tests using a test runner.</span></span>                                     |

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="bfb56-244">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="bfb56-244">.NET Core 1.x</span></span>](#tab/netcore1x)

| <span data-ttu-id="bfb56-245">Polecenie</span><span class="sxs-lookup"><span data-stu-id="bfb56-245">Command</span></span>                             | <span data-ttu-id="bfb56-246">Funkcja</span><span class="sxs-lookup"><span data-stu-id="bfb56-246">Function</span></span>                                                            |
| ----------------------------------- | ------------------------------------------------------------------- |
| [<span data-ttu-id="bfb56-247">dotnet build</span><span class="sxs-lookup"><span data-stu-id="bfb56-247">dotnet build</span></span>](dotnet-build.md)     | <span data-ttu-id="bfb56-248">Kompiluje aplikację platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="bfb56-248">Builds a .NET Core application.</span></span>                                     |
| [<span data-ttu-id="bfb56-249">dotnet clean</span><span class="sxs-lookup"><span data-stu-id="bfb56-249">dotnet clean</span></span>](dotnet-clean.md)     | <span data-ttu-id="bfb56-250">Czyste dane wyjściowe kompilacji.</span><span class="sxs-lookup"><span data-stu-id="bfb56-250">Clean build outputs.</span></span>                                              |
| [<span data-ttu-id="bfb56-251">dotnet migrate</span><span class="sxs-lookup"><span data-stu-id="bfb56-251">dotnet migrate</span></span>](dotnet-migrate.md) | <span data-ttu-id="bfb56-252">Migruje prawidłowy projekt w wersji zapoznawczej 2 do projektu zestaw .NET Core SDK 1,0.</span><span class="sxs-lookup"><span data-stu-id="bfb56-252">Migrates a valid Preview 2 project to a .NET Core SDK 1.0 project.</span></span>  |
| [<span data-ttu-id="bfb56-253">dotnet msbuild</span><span class="sxs-lookup"><span data-stu-id="bfb56-253">dotnet msbuild</span></span>](dotnet-msbuild.md) | <span data-ttu-id="bfb56-254">Zapewnia dostęp do wiersza polecenia programu MSBuild.</span><span class="sxs-lookup"><span data-stu-id="bfb56-254">Provides access to the MSBuild command line.</span></span>                        |
| [<span data-ttu-id="bfb56-255">dotnet new</span><span class="sxs-lookup"><span data-stu-id="bfb56-255">dotnet new</span></span>](dotnet-new.md)         | <span data-ttu-id="bfb56-256">Inicjuje projekt C# lub F# dla danego szablonu.</span><span class="sxs-lookup"><span data-stu-id="bfb56-256">Initializes a C# or F# project for a given template.</span></span>                |
| [<span data-ttu-id="bfb56-257">dotnet pack</span><span class="sxs-lookup"><span data-stu-id="bfb56-257">dotnet pack</span></span>](dotnet-pack.md)       | <span data-ttu-id="bfb56-258">Tworzy pakiet NuGet kodu.</span><span class="sxs-lookup"><span data-stu-id="bfb56-258">Creates a NuGet package of your code.</span></span>                               |
| [<span data-ttu-id="bfb56-259">dotnet publish</span><span class="sxs-lookup"><span data-stu-id="bfb56-259">dotnet publish</span></span>](dotnet-publish.md) | <span data-ttu-id="bfb56-260">Publikuje zależne od programu .NET Framework lub samodzielną aplikację.</span><span class="sxs-lookup"><span data-stu-id="bfb56-260">Publishes a .NET framework-dependent or self-contained application.</span></span> |
| [<span data-ttu-id="bfb56-261">dotnet restore</span><span class="sxs-lookup"><span data-stu-id="bfb56-261">dotnet restore</span></span>](dotnet-restore.md) | <span data-ttu-id="bfb56-262">Przywraca zależności dla danej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="bfb56-262">Restores the dependencies for a given application.</span></span>                  |
| [<span data-ttu-id="bfb56-263">dotnet run</span><span class="sxs-lookup"><span data-stu-id="bfb56-263">dotnet run</span></span>](dotnet-run.md)         | <span data-ttu-id="bfb56-264">Uruchamia aplikację ze źródła.</span><span class="sxs-lookup"><span data-stu-id="bfb56-264">Runs the application from source.</span></span>                                   |
| [<span data-ttu-id="bfb56-265">dotnet sln</span><span class="sxs-lookup"><span data-stu-id="bfb56-265">dotnet sln</span></span>](dotnet-sln.md)         | <span data-ttu-id="bfb56-266">Opcje dodawania, usuwania i wyświetlania listy projektów w pliku rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="bfb56-266">Options to add, remove, and list projects in a solution file.</span></span>       |
| [<span data-ttu-id="bfb56-267">dotnet test</span><span class="sxs-lookup"><span data-stu-id="bfb56-267">dotnet test</span></span>](dotnet-test.md)       | <span data-ttu-id="bfb56-268">Uruchamia testy przy użyciu modułu uruchamiającego testy.</span><span class="sxs-lookup"><span data-stu-id="bfb56-268">Runs tests using a test runner.</span></span>                                     |

---

### <a name="project-references"></a><span data-ttu-id="bfb56-269">Odwołania projektu</span><span class="sxs-lookup"><span data-stu-id="bfb56-269">Project references</span></span>

<span data-ttu-id="bfb56-270">Polecenie</span><span class="sxs-lookup"><span data-stu-id="bfb56-270">Command</span></span> | <span data-ttu-id="bfb56-271">Funkcja</span><span class="sxs-lookup"><span data-stu-id="bfb56-271">Function</span></span>
--- | ---
[<span data-ttu-id="bfb56-272">dotnet add reference</span><span class="sxs-lookup"><span data-stu-id="bfb56-272">dotnet add reference</span></span>](dotnet-add-reference.md) | <span data-ttu-id="bfb56-273">Dodaje odwołanie do projektu.</span><span class="sxs-lookup"><span data-stu-id="bfb56-273">Adds a project reference.</span></span>
[<span data-ttu-id="bfb56-274">dotnet list reference</span><span class="sxs-lookup"><span data-stu-id="bfb56-274">dotnet list reference</span></span>](dotnet-list-reference.md) | <span data-ttu-id="bfb56-275">Wyświetla listę odwołań do projektu.</span><span class="sxs-lookup"><span data-stu-id="bfb56-275">Lists project references.</span></span>
[<span data-ttu-id="bfb56-276">dotnet remove reference</span><span class="sxs-lookup"><span data-stu-id="bfb56-276">dotnet remove reference</span></span>](dotnet-remove-reference.md) | <span data-ttu-id="bfb56-277">Usuwa odwołanie do projektu.</span><span class="sxs-lookup"><span data-stu-id="bfb56-277">Removes a project reference.</span></span>

### <a name="nuget-packages"></a><span data-ttu-id="bfb56-278">Pakiety NuGet</span><span class="sxs-lookup"><span data-stu-id="bfb56-278">NuGet packages</span></span>

<span data-ttu-id="bfb56-279">Polecenie</span><span class="sxs-lookup"><span data-stu-id="bfb56-279">Command</span></span> | <span data-ttu-id="bfb56-280">Funkcja</span><span class="sxs-lookup"><span data-stu-id="bfb56-280">Function</span></span>
--- | ---
[<span data-ttu-id="bfb56-281">dotnet add package</span><span class="sxs-lookup"><span data-stu-id="bfb56-281">dotnet add package</span></span>](dotnet-add-package.md) | <span data-ttu-id="bfb56-282">Dodaje pakiet NuGet.</span><span class="sxs-lookup"><span data-stu-id="bfb56-282">Adds a NuGet package.</span></span>
[<span data-ttu-id="bfb56-283">dotnet remove package</span><span class="sxs-lookup"><span data-stu-id="bfb56-283">dotnet remove package</span></span>](dotnet-remove-package.md) | <span data-ttu-id="bfb56-284">Usuwa pakiet NuGet.</span><span class="sxs-lookup"><span data-stu-id="bfb56-284">Removes a NuGet package.</span></span>

### <a name="nuget-commands"></a><span data-ttu-id="bfb56-285">Polecenia NuGet</span><span class="sxs-lookup"><span data-stu-id="bfb56-285">NuGet commands</span></span>

<span data-ttu-id="bfb56-286">Polecenie</span><span class="sxs-lookup"><span data-stu-id="bfb56-286">Command</span></span> | <span data-ttu-id="bfb56-287">Funkcja</span><span class="sxs-lookup"><span data-stu-id="bfb56-287">Function</span></span>
--- | ---
[<span data-ttu-id="bfb56-288">dotnet nuget delete</span><span class="sxs-lookup"><span data-stu-id="bfb56-288">dotnet nuget delete</span></span>](dotnet-nuget-delete.md) | <span data-ttu-id="bfb56-289">Usuwa pakiet z serwera lub go wystawia.</span><span class="sxs-lookup"><span data-stu-id="bfb56-289">Deletes or unlists a package from the server.</span></span>
[<span data-ttu-id="bfb56-290">dotnet nuget locals</span><span class="sxs-lookup"><span data-stu-id="bfb56-290">dotnet nuget locals</span></span>](dotnet-nuget-locals.md) | <span data-ttu-id="bfb56-291">Czyści lub wyświetla lokalne zasoby NuGet, takie jak pamięć podręczna żądań HTTP, tymczasowa pamięć podręczna lub folder pakietów globalnych dla całego komputera.</span><span class="sxs-lookup"><span data-stu-id="bfb56-291">Clears or lists local NuGet resources such as http-request cache, temporary cache, or machine-wide global packages folder.</span></span>
[<span data-ttu-id="bfb56-292">dotnet nuget push</span><span class="sxs-lookup"><span data-stu-id="bfb56-292">dotnet nuget push</span></span>](dotnet-nuget-push.md) | <span data-ttu-id="bfb56-293">Wypchnij pakiet na serwer i opublikuje go.</span><span class="sxs-lookup"><span data-stu-id="bfb56-293">Pushes a package to the server and publishes it.</span></span>

### <a name="global-tools-commands"></a><span data-ttu-id="bfb56-294">Polecenia narzędzi globalnych</span><span class="sxs-lookup"><span data-stu-id="bfb56-294">Global Tools commands</span></span>

<span data-ttu-id="bfb56-295">[Narzędzia globalne platformy .NET Core](global-tools.md) są dostępne począwszy od zestaw .NET Core SDK 2.1.300:</span><span class="sxs-lookup"><span data-stu-id="bfb56-295">[.NET Core Global Tools](global-tools.md) are available starting with .NET Core SDK 2.1.300:</span></span>

<span data-ttu-id="bfb56-296">Polecenie</span><span class="sxs-lookup"><span data-stu-id="bfb56-296">Command</span></span> | <span data-ttu-id="bfb56-297">Funkcja</span><span class="sxs-lookup"><span data-stu-id="bfb56-297">Function</span></span>
--- | ---
[<span data-ttu-id="bfb56-298">dotnet tool install</span><span class="sxs-lookup"><span data-stu-id="bfb56-298">dotnet tool install</span></span>](dotnet-tool-install.md) | <span data-ttu-id="bfb56-299">Instaluje narzędzie globalne na komputerze.</span><span class="sxs-lookup"><span data-stu-id="bfb56-299">Installs a Global Tool on your machine.</span></span>
[<span data-ttu-id="bfb56-300">dotnet tool list</span><span class="sxs-lookup"><span data-stu-id="bfb56-300">dotnet tool list</span></span>](dotnet-tool-list.md) | <span data-ttu-id="bfb56-301">Wyświetla listę wszystkich narzędzi globalnych aktualnie zainstalowanych w domyślnym katalogu na komputerze lub w określonej ścieżce.</span><span class="sxs-lookup"><span data-stu-id="bfb56-301">Lists all Global Tools currently installed in the default directory on your machine or in the specified path.</span></span>
[<span data-ttu-id="bfb56-302">dotnet tool uninstall</span><span class="sxs-lookup"><span data-stu-id="bfb56-302">dotnet tool uninstall</span></span>](dotnet-tool-uninstall.md) | <span data-ttu-id="bfb56-303">Odinstalowuje narzędzie globalne z komputera.</span><span class="sxs-lookup"><span data-stu-id="bfb56-303">Uninstalls a Global Tool from your machine.</span></span>
[<span data-ttu-id="bfb56-304">dotnet tool update</span><span class="sxs-lookup"><span data-stu-id="bfb56-304">dotnet tool update</span></span>](dotnet-tool-update.md) | <span data-ttu-id="bfb56-305">Aktualizuje narzędzie globalne na komputerze.</span><span class="sxs-lookup"><span data-stu-id="bfb56-305">Updates a Global Tool on your machine.</span></span>

### <a name="additional-tools"></a><span data-ttu-id="bfb56-306">Dodatkowe narzędzia</span><span class="sxs-lookup"><span data-stu-id="bfb56-306">Additional tools</span></span>

<span data-ttu-id="bfb56-307">Począwszy od zestaw .NET Core SDK 2.1.300, wiele narzędzi, które były dostępne tylko dla poszczególnych projektów, przy użyciu `DotnetCliToolReference`, są teraz dostępne jako część zestaw .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="bfb56-307">Starting with .NET Core SDK 2.1.300, a number of tools that were available only on a per project basis using `DotnetCliToolReference` are now available as part of the .NET Core SDK.</span></span> <span data-ttu-id="bfb56-308">Te narzędzia są wymienione w poniższej tabeli:</span><span class="sxs-lookup"><span data-stu-id="bfb56-308">These tools are listed in the following table:</span></span>

| <span data-ttu-id="bfb56-309">Narzędzie</span><span class="sxs-lookup"><span data-stu-id="bfb56-309">Tool</span></span>                                              | <span data-ttu-id="bfb56-310">Funkcja</span><span class="sxs-lookup"><span data-stu-id="bfb56-310">Function</span></span>                                                     |
| ------------------------------------------------- | ------------------------------------------------------------ |
| <span data-ttu-id="bfb56-311">dev-certs</span><span class="sxs-lookup"><span data-stu-id="bfb56-311">dev-certs</span></span>                                         | <span data-ttu-id="bfb56-312">Tworzy i zarządza certyfikatami deweloperskimi.</span><span class="sxs-lookup"><span data-stu-id="bfb56-312">Creates and manages development certificates.</span></span>                |
| [<span data-ttu-id="bfb56-313">bieżąco</span><span class="sxs-lookup"><span data-stu-id="bfb56-313">ef</span></span>](/ef/core/miscellaneous/cli/dotnet)           | <span data-ttu-id="bfb56-314">Entity Framework Core narzędzia wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="bfb56-314">Entity Framework Core command-line tools.</span></span>                    |
| <span data-ttu-id="bfb56-315">SQL-pamięć podręczna</span><span class="sxs-lookup"><span data-stu-id="bfb56-315">sql-cache</span></span>                                         | <span data-ttu-id="bfb56-316">SQL Server narzędzia wiersza polecenia pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="bfb56-316">SQL Server cache command-line tools.</span></span>                         |
| [<span data-ttu-id="bfb56-317">wpisy tajne użytkownika</span><span class="sxs-lookup"><span data-stu-id="bfb56-317">user-secrets</span></span>](/aspnet/core/security/app-secrets) | <span data-ttu-id="bfb56-318">Zarządza kluczami tajnymi użytkowników deweloperskich.</span><span class="sxs-lookup"><span data-stu-id="bfb56-318">Manages development user secrets.</span></span>                            |
| [<span data-ttu-id="bfb56-319">Obejrzyj</span><span class="sxs-lookup"><span data-stu-id="bfb56-319">watch</span></span>](/aspnet/core/tutorials/dotnet-watch)      | <span data-ttu-id="bfb56-320">Uruchamia obserwatora plików, który uruchamia polecenie, gdy pliki zmienią się.</span><span class="sxs-lookup"><span data-stu-id="bfb56-320">Starts a file watcher that runs a command when files change.</span></span> |

<span data-ttu-id="bfb56-321">Aby uzyskać więcej informacji na temat każdego narzędzia, wpisz `dotnet <tool-name> --help`.</span><span class="sxs-lookup"><span data-stu-id="bfb56-321">For more information about each tool, type `dotnet <tool-name> --help`.</span></span>

## <a name="examples"></a><span data-ttu-id="bfb56-322">Przykłady</span><span class="sxs-lookup"><span data-stu-id="bfb56-322">Examples</span></span>

<span data-ttu-id="bfb56-323">Tworzy nową aplikację konsolową platformy .NET Core:</span><span class="sxs-lookup"><span data-stu-id="bfb56-323">Creates a new .NET Core console application:</span></span>

`dotnet new console`

<span data-ttu-id="bfb56-324">Przywróć zależności dla danej aplikacji:</span><span class="sxs-lookup"><span data-stu-id="bfb56-324">Restore dependencies for a given application:</span></span>

`dotnet restore`

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

<span data-ttu-id="bfb56-325">Kompiluj projekt i jego zależności w danym katalogu:</span><span class="sxs-lookup"><span data-stu-id="bfb56-325">Build a project and its dependencies in a given directory:</span></span>

`dotnet build`

<span data-ttu-id="bfb56-326">Uruchom bibliotekę DLL aplikacji, taką jak `myapp.dll`:</span><span class="sxs-lookup"><span data-stu-id="bfb56-326">Run an application DLL, such as `myapp.dll`:</span></span>

`dotnet myapp.dll`

## <a name="environment-variables"></a><span data-ttu-id="bfb56-327">Zmienne środowiskowe</span><span class="sxs-lookup"><span data-stu-id="bfb56-327">Environment variables</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="bfb56-328">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="bfb56-328">.NET Core 2.1</span></span>](#tab/netcore21)

`DOTNET_PACKAGES`

<span data-ttu-id="bfb56-329">Folder pakiety globalne.</span><span class="sxs-lookup"><span data-stu-id="bfb56-329">The global packages folder.</span></span> <span data-ttu-id="bfb56-330">Jeśli nie zostanie ustawiona, domyślnie jest `~/.nuget/packages` w systemie UNIX lub `%userprofile%\.nuget\packages` na komputerze z systemem Windows.</span><span class="sxs-lookup"><span data-stu-id="bfb56-330">If not set, it defaults to `~/.nuget/packages` on Unix or `%userprofile%\.nuget\packages` on Windows.</span></span>

`DOTNET_SERVICING`

<span data-ttu-id="bfb56-331">Określa lokalizację indeksu obsługi, który ma być używany przez host udostępniony podczas ładowania środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="bfb56-331">Specifies the location of the servicing index to use by the shared host when loading the runtime.</span></span>

`DOTNET_CLI_TELEMETRY_OPTOUT`

<span data-ttu-id="bfb56-332">Określa, czy dane dotyczące użycia narzędzi .NET Core są zbierane i wysyłane do firmy Microsoft.</span><span class="sxs-lookup"><span data-stu-id="bfb56-332">Specifies whether data about the .NET Core tools usage is collected and sent to Microsoft.</span></span> <span data-ttu-id="bfb56-333">Ustaw `true`, aby zrezygnować z funkcji telemetrii (wartości `true`, `1`lub `yes` zaakceptowane).</span><span class="sxs-lookup"><span data-stu-id="bfb56-333">Set to `true` to opt-out of the telemetry feature (values `true`, `1`, or `yes` accepted).</span></span> <span data-ttu-id="bfb56-334">W przeciwnym razie ustaw wartość `false`, aby zrezygnować z funkcji telemetrii (wartości `false`, `0`lub `no` zaakceptowane).</span><span class="sxs-lookup"><span data-stu-id="bfb56-334">Otherwise, set to `false` to opt into the telemetry features (values `false`, `0`, or `no` accepted).</span></span> <span data-ttu-id="bfb56-335">Jeśli nie zostanie ustawiona, wartość domyślna to `false` i aktywna jest funkcja telemetrii.</span><span class="sxs-lookup"><span data-stu-id="bfb56-335">If not set, the default is `false` and the telemetry feature is active.</span></span>

`DOTNET_MULTILEVEL_LOOKUP`

<span data-ttu-id="bfb56-336">Określa, czy środowisko uruchomieniowe programu .NET Core, udostępnione środowisko lub zestaw SDK są rozpoznawane z lokalizacji globalnej.</span><span class="sxs-lookup"><span data-stu-id="bfb56-336">Specifies whether .NET Core runtime, shared framework, or SDK are resolved from the global location.</span></span> <span data-ttu-id="bfb56-337">Jeśli nie zostanie ustawiona, domyślnie `true`.</span><span class="sxs-lookup"><span data-stu-id="bfb56-337">If not set, it defaults to `true`.</span></span> <span data-ttu-id="bfb56-338">Ustaw `false`, aby nie rozwiązany z lokalizacji globalnej i mieć izolowane instalacje platformy .NET Core (wartości `0` lub `false` są akceptowane).</span><span class="sxs-lookup"><span data-stu-id="bfb56-338">Set to `false` to not resolve from the global location and have isolated .NET Core installations (values `0` or `false` are accepted).</span></span> <span data-ttu-id="bfb56-339">Aby uzyskać więcej informacji o wyszukiwaniu wielu poziomów, zobacz [SharedFX wyszukiwanie na wielu poziomach](https://github.com/dotnet/core-setup/blob/master/Documentation/design-docs/multilevel-sharedfx-lookup.md).</span><span class="sxs-lookup"><span data-stu-id="bfb56-339">For more information about multi-level lookup, see [Multi-level SharedFX Lookup](https://github.com/dotnet/core-setup/blob/master/Documentation/design-docs/multilevel-sharedfx-lookup.md).</span></span>

`DOTNET_ROLL_FORWARD_ON_NO_CANDIDATE_FX`

<span data-ttu-id="bfb56-340">Wyłącza opcję wycofywania wersji pomocniczej, jeśli jest ustawiona na `0`.</span><span class="sxs-lookup"><span data-stu-id="bfb56-340">Disables minor version roll forward, if set to `0`.</span></span> <span data-ttu-id="bfb56-341">Aby uzyskać więcej informacji, zobacz [przewinięcie do przodu](../whats-new/dotnet-core-2-1.md#roll-forward).</span><span class="sxs-lookup"><span data-stu-id="bfb56-341">For more information, see [Roll forward](../whats-new/dotnet-core-2-1.md#roll-forward).</span></span>

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="bfb56-342">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="bfb56-342">.NET Core 2.0</span></span>](#tab/netcore20)

`DOTNET_PACKAGES`

<span data-ttu-id="bfb56-343">Podstawowa pamięć podręczna pakietu.</span><span class="sxs-lookup"><span data-stu-id="bfb56-343">The primary package cache.</span></span> <span data-ttu-id="bfb56-344">Jeśli nie zostanie ustawiona, domyślnie jest `$HOME/.nuget/packages` w systemie UNIX lub `%userprofile%\.nuget\packages` na komputerze z systemem Windows.</span><span class="sxs-lookup"><span data-stu-id="bfb56-344">If not set, it defaults to `$HOME/.nuget/packages` on Unix or `%userprofile%\.nuget\packages` on Windows.</span></span>

`DOTNET_SERVICING`

<span data-ttu-id="bfb56-345">Określa lokalizację indeksu obsługi, który ma być używany przez host udostępniony podczas ładowania środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="bfb56-345">Specifies the location of the servicing index to use by the shared host when loading the runtime.</span></span>

`DOTNET_CLI_TELEMETRY_OPTOUT`

<span data-ttu-id="bfb56-346">Określa, czy dane dotyczące użycia narzędzi .NET Core są zbierane i wysyłane do firmy Microsoft.</span><span class="sxs-lookup"><span data-stu-id="bfb56-346">Specifies whether data about the .NET Core tools usage is collected and sent to Microsoft.</span></span> <span data-ttu-id="bfb56-347">Ustaw `true`, aby zrezygnować z funkcji telemetrii (wartości `true`, `1`lub `yes` zaakceptowane).</span><span class="sxs-lookup"><span data-stu-id="bfb56-347">Set to `true` to opt-out of the telemetry feature (values `true`, `1`, or `yes` accepted).</span></span> <span data-ttu-id="bfb56-348">W przeciwnym razie ustaw wartość `false`, aby zrezygnować z funkcji telemetrii (wartości `false`, `0`lub `no` zaakceptowane).</span><span class="sxs-lookup"><span data-stu-id="bfb56-348">Otherwise, set to `false` to opt into the telemetry features (values `false`, `0`, or `no` accepted).</span></span> <span data-ttu-id="bfb56-349">Jeśli nie zostanie ustawiona, wartość domyślna to `false` i aktywna jest funkcja telemetrii.</span><span class="sxs-lookup"><span data-stu-id="bfb56-349">If not set, the default is `false` and the telemetry feature is active.</span></span>

`DOTNET_MULTILEVEL_LOOKUP`

<span data-ttu-id="bfb56-350">Określa, czy środowisko uruchomieniowe programu .NET Core, udostępnione środowisko lub zestaw SDK są rozpoznawane z lokalizacji globalnej.</span><span class="sxs-lookup"><span data-stu-id="bfb56-350">Specifies whether .NET Core runtime, shared framework, or SDK are resolved from the global location.</span></span> <span data-ttu-id="bfb56-351">Jeśli nie zostanie ustawiona, domyślnie `true`.</span><span class="sxs-lookup"><span data-stu-id="bfb56-351">If not set, it defaults to `true`.</span></span> <span data-ttu-id="bfb56-352">Ustaw `false`, aby nie rozwiązany z lokalizacji globalnej i mieć izolowane instalacje platformy .NET Core (wartości `0` lub `false` są akceptowane).</span><span class="sxs-lookup"><span data-stu-id="bfb56-352">Set to `false` to not resolve from the global location and have isolated .NET Core installations (values `0` or `false` are accepted).</span></span> <span data-ttu-id="bfb56-353">Aby uzyskać więcej informacji o wyszukiwaniu wielu poziomów, zobacz [SharedFX wyszukiwanie na wielu poziomach](https://github.com/dotnet/core-setup/blob/master/Documentation/design-docs/multilevel-sharedfx-lookup.md).</span><span class="sxs-lookup"><span data-stu-id="bfb56-353">For more information about multi-level lookup, see [Multi-level SharedFX Lookup](https://github.com/dotnet/core-setup/blob/master/Documentation/design-docs/multilevel-sharedfx-lookup.md).</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="bfb56-354">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="bfb56-354">.NET Core 1.x</span></span>](#tab/netcore1x)

`DOTNET_PACKAGES`

<span data-ttu-id="bfb56-355">Podstawowa pamięć podręczna pakietu.</span><span class="sxs-lookup"><span data-stu-id="bfb56-355">The primary package cache.</span></span> <span data-ttu-id="bfb56-356">Jeśli nie zostanie ustawiona, domyślnie jest `$HOME/.nuget/packages` w systemie UNIX lub `%userprofile%\.nuget\packages` na komputerze z systemem Windows.</span><span class="sxs-lookup"><span data-stu-id="bfb56-356">If not set, it defaults to `$HOME/.nuget/packages` on Unix or `%userprofile%\.nuget\packages` on Windows.</span></span>

`DOTNET_SERVICING`

<span data-ttu-id="bfb56-357">Określa lokalizację indeksu obsługi, który ma być używany przez host udostępniony podczas ładowania środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="bfb56-357">Specifies the location of the servicing index to use by the shared host when loading the runtime.</span></span>

`DOTNET_CLI_TELEMETRY_OPTOUT`

<span data-ttu-id="bfb56-358">Określa, czy dane dotyczące użycia narzędzi .NET Core są zbierane i wysyłane do firmy Microsoft.</span><span class="sxs-lookup"><span data-stu-id="bfb56-358">Specifies whether data about the .NET Core tools usage is collected and sent to Microsoft.</span></span> <span data-ttu-id="bfb56-359">Ustaw `true`, aby zrezygnować z funkcji telemetrii (wartości `true`, `1`lub `yes` zaakceptowane).</span><span class="sxs-lookup"><span data-stu-id="bfb56-359">Set to `true` to opt-out of the telemetry feature (values `true`, `1`, or `yes` accepted).</span></span> <span data-ttu-id="bfb56-360">W przeciwnym razie ustaw wartość `false`, aby zrezygnować z funkcji telemetrii (wartości `false`, `0`lub `no` zaakceptowane).</span><span class="sxs-lookup"><span data-stu-id="bfb56-360">Otherwise, set to `false` to opt into the telemetry features (values `false`, `0`, or `no` accepted).</span></span> <span data-ttu-id="bfb56-361">Jeśli nie zostanie ustawiona, wartość domyślna to `false` i aktywna jest funkcja telemetrii.</span><span class="sxs-lookup"><span data-stu-id="bfb56-361">If not set, the default is `false` and the telemetry feature is active.</span></span>

---

## <a name="see-also"></a><span data-ttu-id="bfb56-362">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="bfb56-362">See also</span></span>

- [<span data-ttu-id="bfb56-363">Pliki konfiguracji środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="bfb56-363">Runtime Configuration Files</span></span>](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md)
- [<span data-ttu-id="bfb56-364">Ustawienia konfiguracji środowiska uruchomieniowego .NET Core</span><span class="sxs-lookup"><span data-stu-id="bfb56-364">.NET Core run-time configuration settings</span></span>](../run-time-config/index.md)
