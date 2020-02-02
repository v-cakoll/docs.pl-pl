---
title: dotnet — polecenie
description: Dowiedz się więcej na temat polecenia dotnet (sterownika generycznego dla interfejs wiersza polecenia platformy .NET Core) i jego użycia.
ms.date: 06/04/2018
ms.openlocfilehash: 7674529980623caa2291987bdeba52f50ce2fc2c
ms.sourcegitcommit: cdf5084648bf5e77970cbfeaa23f1cab3e6e234e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/01/2020
ms.locfileid: "76920548"
---
# <a name="dotnet-command"></a><span data-ttu-id="b9e97-103">dotnet — polecenie</span><span class="sxs-lookup"><span data-stu-id="b9e97-103">dotnet command</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="b9e97-104">Nazwa</span><span class="sxs-lookup"><span data-stu-id="b9e97-104">Name</span></span>

<span data-ttu-id="b9e97-105">`dotnet` — narzędzie do zarządzania kodem źródłowym i plikami binarnymi platformy .NET.</span><span class="sxs-lookup"><span data-stu-id="b9e97-105">`dotnet` - A tool for managing .NET source code and binaries.</span></span>

## <a name="synopsis"></a><span data-ttu-id="b9e97-106">Streszczenie</span><span class="sxs-lookup"><span data-stu-id="b9e97-106">Synopsis</span></span>

<!-- markdownlint-disable MD025 -->

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="b9e97-107">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="b9e97-107">.NET Core 2.1</span></span>](#tab/netcore21)

```dotnetcli
dotnet [command] [arguments] [--additional-deps] [--additionalprobingpath] [--depsfile]
    [-d|--diagnostics] [--fx-version] [-h|--help] [--info] [--list-runtimes] [--list-sdks] [--roll-forward-on-no-candidate-fx] [--runtimeconfig] [-v|--verbosity] [--version]
```

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="b9e97-108">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="b9e97-108">.NET Core 2.0</span></span>](#tab/netcore20)

```dotnetcli
dotnet [command] [arguments] [--additional-deps] [--additionalprobingpath] [--depsfile]
    [-d|--diagnostics] [--fx-version] [-h|--help] [--info] [--roll-forward-on-no-candidate-fx]
    [--runtimeconfig] [-v|--verbosity] [--version]
```

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="b9e97-109">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="b9e97-109">.NET Core 1.x</span></span>](#tab/netcore1x)

```dotnetcli
dotnet [command] [arguments] [--additionalprobingpath] [--depsfile] [-d|--diagnostics]
    [--fx-version] [-h|--help] [--info] [--runtimeconfig] [-v|--verbosity] [--version]
```

---

## <a name="description"></a><span data-ttu-id="b9e97-110">Opis</span><span class="sxs-lookup"><span data-stu-id="b9e97-110">Description</span></span>

<span data-ttu-id="b9e97-111">`dotnet` jest narzędziem do zarządzania kodem źródłowym i plikami binarnymi programu .NET.</span><span class="sxs-lookup"><span data-stu-id="b9e97-111">`dotnet` is a tool for managing .NET source code and binaries.</span></span> <span data-ttu-id="b9e97-112">Udostępnia polecenia wykonujące określone zadania, takie jak [`dotnet build`](dotnet-build.md) i [`dotnet run`](dotnet-run.md).</span><span class="sxs-lookup"><span data-stu-id="b9e97-112">It exposes commands that perform specific tasks, such as [`dotnet build`](dotnet-build.md) and [`dotnet run`](dotnet-run.md).</span></span> <span data-ttu-id="b9e97-113">Każde polecenie definiuje własne argumenty.</span><span class="sxs-lookup"><span data-stu-id="b9e97-113">Each command defines its own arguments.</span></span> <span data-ttu-id="b9e97-114">Wpisz `--help` po każdym poleceniu, aby uzyskać dostęp do krótkiej dokumentacji pomocy.</span><span class="sxs-lookup"><span data-stu-id="b9e97-114">Type `--help` after each command to access brief help documentation.</span></span>

<span data-ttu-id="b9e97-115">`dotnet` można używać do uruchamiania aplikacji przez określenie biblioteki DLL aplikacji, takiej jak `dotnet myapp.dll`.</span><span class="sxs-lookup"><span data-stu-id="b9e97-115">`dotnet` can be used to run applications, by specifying an application DLL, such as `dotnet myapp.dll`.</span></span> <span data-ttu-id="b9e97-116">Zobacz [wdrażanie aplikacji .NET Core](../deploying/index.md) w celu uzyskania informacji na temat opcji wdrażania.</span><span class="sxs-lookup"><span data-stu-id="b9e97-116">See [.NET Core application deployment](../deploying/index.md) for to learn about deployment options.</span></span>

## <a name="options"></a><span data-ttu-id="b9e97-117">Opcje</span><span class="sxs-lookup"><span data-stu-id="b9e97-117">Options</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="b9e97-118">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="b9e97-118">.NET Core 2.1</span></span>](#tab/netcore21)

`--additional-deps <PATH>`

<span data-ttu-id="b9e97-119">Ścieżka do dodatkowego pliku *. deps. JSON* .</span><span class="sxs-lookup"><span data-stu-id="b9e97-119">Path to an additional *.deps.json* file.</span></span>

`--additionalprobingpath <PATH>`

<span data-ttu-id="b9e97-120">Ścieżka zawierająca zasady i zestawy do sondowania.</span><span class="sxs-lookup"><span data-stu-id="b9e97-120">Path containing probing policy and assemblies to probe.</span></span>

`--depsfile`

<span data-ttu-id="b9e97-121">Ścieżka do pliku *deps. JSON* .</span><span class="sxs-lookup"><span data-stu-id="b9e97-121">Path to a *deps.json* file.</span></span>

<span data-ttu-id="b9e97-122">Plik *deps. JSON* zawiera listę zależności, zależności kompilacji i informacje o wersji używane do rozwiązywania konfliktów zestawów.</span><span class="sxs-lookup"><span data-stu-id="b9e97-122">A *deps.json* file contains a list of dependencies, compilation dependencies, and version information used to address assembly conflicts.</span></span> <span data-ttu-id="b9e97-123">Aby uzyskać więcej informacji na temat tego pliku, zobacz [pliki konfiguracji środowiska uruchomieniowego](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md) w serwisie GitHub.</span><span class="sxs-lookup"><span data-stu-id="b9e97-123">For more information about this file, see [Runtime Configuration Files](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md) on GitHub.</span></span>

`-d|--diagnostics`

<span data-ttu-id="b9e97-124">Włącza diagnostykę danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="b9e97-124">Enables diagnostic output.</span></span>

`--fx-version <VERSION>`

<span data-ttu-id="b9e97-125">Wersja środowiska uruchomieniowego platformy .NET Core do użycia w celu uruchomienia aplikacji.</span><span class="sxs-lookup"><span data-stu-id="b9e97-125">Version of the .NET Core runtime to use to run the application.</span></span>

`-h|--help`

<span data-ttu-id="b9e97-126">Drukuje dokumentację dla danego polecenia, taką jak `dotnet build --help`.</span><span class="sxs-lookup"><span data-stu-id="b9e97-126">Prints out documentation for a given command, such as `dotnet build --help`.</span></span> <span data-ttu-id="b9e97-127">`dotnet --help` drukuje listę dostępnych poleceń.</span><span class="sxs-lookup"><span data-stu-id="b9e97-127">`dotnet --help` prints a list of available commands.</span></span>

`--info`

<span data-ttu-id="b9e97-128">Drukuje szczegółowe informacje na temat instalacji programu .NET Core i środowiska maszynowego, takiego jak bieżący system operacyjny, i zatwierdzania SHA dla wersji .NET Core.</span><span class="sxs-lookup"><span data-stu-id="b9e97-128">Prints out detailed information about a .NET Core installation and the machine environment, such as the current operating system, and commit SHA of the .NET Core version.</span></span>

`--list-runtimes`

<span data-ttu-id="b9e97-129">Wyświetla zainstalowane środowiska uruchomieniowe platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="b9e97-129">Displays the installed .NET Core runtimes.</span></span>

`--list-sdks`

<span data-ttu-id="b9e97-130">Wyświetla zainstalowane zestawy SDK platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="b9e97-130">Displays the installed .NET Core SDKs.</span></span>

`--roll-forward-on-no-candidate-fx <N>`

<span data-ttu-id="b9e97-131">Definiuje zachowanie, gdy wymagana architektura udostępniona jest niedostępna.</span><span class="sxs-lookup"><span data-stu-id="b9e97-131">Defines behavior when the required shared framework is not available.</span></span> <span data-ttu-id="b9e97-132">`N` może być:</span><span class="sxs-lookup"><span data-stu-id="b9e97-132">`N` can be:</span></span>

- <span data-ttu-id="b9e97-133">`0` — Wyłącz nawet dodatkową wersję pomocniczą.</span><span class="sxs-lookup"><span data-stu-id="b9e97-133">`0` - Disable even minor version roll forward.</span></span>
- <span data-ttu-id="b9e97-134">`1` — przewinięcie do wersji pomocniczej, ale nie w wersji głównej.</span><span class="sxs-lookup"><span data-stu-id="b9e97-134">`1` - Roll forward on minor version, but not on major version.</span></span> <span data-ttu-id="b9e97-135">Jest to zachowanie domyślne.</span><span class="sxs-lookup"><span data-stu-id="b9e97-135">This is the default behavior.</span></span>
- <span data-ttu-id="b9e97-136">`2` — przewinięcie w przód do wersji pomocniczych i głównych.</span><span class="sxs-lookup"><span data-stu-id="b9e97-136">`2` - Roll forward on minor and major versions.</span></span>

 <span data-ttu-id="b9e97-137">Aby uzyskać więcej informacji, zobacz [przewinięcie do przodu](../whats-new/dotnet-core-2-1.md#roll-forward).</span><span class="sxs-lookup"><span data-stu-id="b9e97-137">For more information, see [Roll forward](../whats-new/dotnet-core-2-1.md#roll-forward).</span></span>

`--runtimeconfig`

<span data-ttu-id="b9e97-138">Ścieżka do pliku *runtimeconfig. JSON* .</span><span class="sxs-lookup"><span data-stu-id="b9e97-138">Path to a *runtimeconfig.json* file.</span></span>

<span data-ttu-id="b9e97-139">Plik *runtimeconfig. JSON* to plik konfiguracji zawierający ustawienia czasu wykonywania.</span><span class="sxs-lookup"><span data-stu-id="b9e97-139">A *runtimeconfig.json* file is a configuration file containing run-time settings.</span></span> <span data-ttu-id="b9e97-140">Aby uzyskać więcej informacji, zobacz [Ustawienia konfiguracji środowiska uruchomieniowego .NET Core](../run-time-config/index.md#runtimeconfigjson).</span><span class="sxs-lookup"><span data-stu-id="b9e97-140">For more information, see [.NET Core run-time configuration settings](../run-time-config/index.md#runtimeconfigjson).</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="b9e97-141">Ustawia poziom szczegółowości polecenia.</span><span class="sxs-lookup"><span data-stu-id="b9e97-141">Sets the verbosity level of the command.</span></span> <span data-ttu-id="b9e97-142">Dozwolone wartości to `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`i `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="b9e97-142">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="b9e97-143">Nieobsługiwane w każdym poleceniu; Aby określić, czy ta opcja jest dostępna, zobacz określoną stronę poleceń.</span><span class="sxs-lookup"><span data-stu-id="b9e97-143">Not supported in every command; see specific command page to determine if this option is available.</span></span>

`--version`

<span data-ttu-id="b9e97-144">Drukuje używaną wersję zestaw .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="b9e97-144">Prints out the version of the .NET Core SDK in use.</span></span>

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="b9e97-145">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="b9e97-145">.NET Core 2.0</span></span>](#tab/netcore20)

`--additional-deps <PATH>`

<span data-ttu-id="b9e97-146">Ścieżka do dodatkowego pliku *. deps. JSON* .</span><span class="sxs-lookup"><span data-stu-id="b9e97-146">Path to an additional *.deps.json* file.</span></span>

`--additionalprobingpath <PATH>`

<span data-ttu-id="b9e97-147">Ścieżka zawierająca zasady i zestawy do sondowania.</span><span class="sxs-lookup"><span data-stu-id="b9e97-147">Path containing probing policy and assemblies to probe.</span></span>

`--depsfile`

<span data-ttu-id="b9e97-148">Ścieżka do pliku *deps. JSON* .</span><span class="sxs-lookup"><span data-stu-id="b9e97-148">Path to a *deps.json* file.</span></span>

<span data-ttu-id="b9e97-149">Plik *deps. JSON* zawiera listę zależności, zależności kompilacji i informacje o wersji używane do rozwiązywania konfliktów zestawów.</span><span class="sxs-lookup"><span data-stu-id="b9e97-149">A *deps.json* file contains a list of dependencies, compilation dependencies and version information used to address assembly conflicts.</span></span> <span data-ttu-id="b9e97-150">Aby uzyskać więcej informacji na temat tego pliku, zobacz [pliki konfiguracji środowiska uruchomieniowego w serwisie GitHub](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md).</span><span class="sxs-lookup"><span data-stu-id="b9e97-150">For more details on this file, see [Runtime Configuration Files on GitHub](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md).</span></span>

`-d|--diagnostics`

<span data-ttu-id="b9e97-151">Włącza diagnostykę danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="b9e97-151">Enables diagnostic output.</span></span>

`--fx-version <VERSION>`

<span data-ttu-id="b9e97-152">Wersja środowiska uruchomieniowego platformy .NET Core do użycia w celu uruchomienia aplikacji.</span><span class="sxs-lookup"><span data-stu-id="b9e97-152">Version of the .NET Core runtime to use to run the application.</span></span>

`-h|--help`

<span data-ttu-id="b9e97-153">Drukuje dokumentację dla danego polecenia, taką jak `dotnet build --help`.</span><span class="sxs-lookup"><span data-stu-id="b9e97-153">Prints out documentation for a given command, such as `dotnet build --help`.</span></span> <span data-ttu-id="b9e97-154">`dotnet --help` drukuje listę dostępnych poleceń.</span><span class="sxs-lookup"><span data-stu-id="b9e97-154">`dotnet --help` prints a list of available commands.</span></span>

`--info`

<span data-ttu-id="b9e97-155">Drukuje szczegółowe informacje na temat instalacji programu .NET Core i środowiska maszynowego, takiego jak bieżący system operacyjny, i zatwierdzania SHA dla wersji .NET Core.</span><span class="sxs-lookup"><span data-stu-id="b9e97-155">Prints out detailed information about a .NET Core installation and the machine environment, such as the current operating system, and commit SHA of the .NET Core version.</span></span>

`--roll-forward-on-no-candidate-fx`

 <span data-ttu-id="b9e97-156">Wyłącza opcję wycofywania wersji pomocniczej, jeśli jest ustawiona na `0`.</span><span class="sxs-lookup"><span data-stu-id="b9e97-156">Disables minor version roll forward, if set to `0`.</span></span> <span data-ttu-id="b9e97-157">Aby uzyskać więcej informacji, zobacz [przewinięcie do przodu](../whats-new/dotnet-core-2-1.md#roll-forward).</span><span class="sxs-lookup"><span data-stu-id="b9e97-157">For more information, see [Roll forward](../whats-new/dotnet-core-2-1.md#roll-forward).</span></span>

`--runtimeconfig`

<span data-ttu-id="b9e97-158">Ścieżka do pliku *runtimeconfig. JSON* .</span><span class="sxs-lookup"><span data-stu-id="b9e97-158">Path to a *runtimeconfig.json* file.</span></span>

<span data-ttu-id="b9e97-159">Plik *runtimeconfig. JSON* to plik konfiguracji zawierający ustawienia czasu wykonywania.</span><span class="sxs-lookup"><span data-stu-id="b9e97-159">A *runtimeconfig.json* file is a configuration file containing run-time settings.</span></span> <span data-ttu-id="b9e97-160">Aby uzyskać więcej informacji, zobacz [Ustawienia konfiguracji środowiska uruchomieniowego .NET Core](../run-time-config/index.md#runtimeconfigjson).</span><span class="sxs-lookup"><span data-stu-id="b9e97-160">For more information, see [.NET Core run-time configuration settings](../run-time-config/index.md#runtimeconfigjson).</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="b9e97-161">Ustawia poziom szczegółowości polecenia.</span><span class="sxs-lookup"><span data-stu-id="b9e97-161">Sets the verbosity level of the command.</span></span> <span data-ttu-id="b9e97-162">Dozwolone wartości to `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`i `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="b9e97-162">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="b9e97-163">Nieobsługiwane w każdym poleceniu; Aby określić, czy ta opcja jest dostępna, zobacz określoną stronę poleceń.</span><span class="sxs-lookup"><span data-stu-id="b9e97-163">Not supported in every command; see specific command page to determine if this option is available.</span></span>

`--version`

<span data-ttu-id="b9e97-164">Drukuje używaną wersję zestaw .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="b9e97-164">Prints out the version of the .NET Core SDK in use.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="b9e97-165">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="b9e97-165">.NET Core 1.x</span></span>](#tab/netcore1x)

`--additionalprobingpath <PATH>`

<span data-ttu-id="b9e97-166">Ścieżka zawierająca zasady i zestawy do sondowania.</span><span class="sxs-lookup"><span data-stu-id="b9e97-166">Path containing probing policy and assemblies to probe.</span></span>

`--depsfile`

<span data-ttu-id="b9e97-167">Ścieżka do pliku *deps. JSON* .</span><span class="sxs-lookup"><span data-stu-id="b9e97-167">Path to a *deps.json* file.</span></span>

<span data-ttu-id="b9e97-168">Plik *deps. JSON* zawiera listę zależności, zależności kompilacji i informacje o wersji używane do rozwiązywania konfliktów zestawów.</span><span class="sxs-lookup"><span data-stu-id="b9e97-168">A *deps.json* file contains a list of dependencies, compilation dependencies and version information used to address assembly conflicts.</span></span> <span data-ttu-id="b9e97-169">Aby uzyskać więcej informacji na temat tego pliku, zobacz [pliki konfiguracji środowiska uruchomieniowego w serwisie GitHub](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md).</span><span class="sxs-lookup"><span data-stu-id="b9e97-169">For more details on this file, see [Runtime Configuration Files on GitHub](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md).</span></span>

`-d|--diagnostics`

<span data-ttu-id="b9e97-170">Włącza diagnostykę danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="b9e97-170">Enables diagnostic output.</span></span>

`--fx-version <VERSION>`

<span data-ttu-id="b9e97-171">Wersja środowiska uruchomieniowego platformy .NET Core do użycia w celu uruchomienia aplikacji.</span><span class="sxs-lookup"><span data-stu-id="b9e97-171">Version of the .NET Core runtime to use to run the application.</span></span>

`-h|--help`

<span data-ttu-id="b9e97-172">Drukuje dokumentację dla danego polecenia, taką jak `dotnet build --help`.</span><span class="sxs-lookup"><span data-stu-id="b9e97-172">Prints out documentation for a given command, such as `dotnet build --help`.</span></span> <span data-ttu-id="b9e97-173">`dotnet --help` drukuje listę dostępnych poleceń.</span><span class="sxs-lookup"><span data-stu-id="b9e97-173">`dotnet --help` prints a list of available commands.</span></span>

`--info`

<span data-ttu-id="b9e97-174">Drukuje szczegółowe informacje na temat instalacji programu .NET Core i środowiska maszynowego, takiego jak bieżący system operacyjny, i zatwierdzania SHA dla wersji .NET Core.</span><span class="sxs-lookup"><span data-stu-id="b9e97-174">Prints out detailed information about a .NET Core installation and the machine environment, such as the current operating system, and commit SHA of the .NET Core version.</span></span>

`--runtimeconfig`

<span data-ttu-id="b9e97-175">Ścieżka do pliku *runtimeconfig. JSON* .</span><span class="sxs-lookup"><span data-stu-id="b9e97-175">Path to a *runtimeconfig.json* file.</span></span>

<span data-ttu-id="b9e97-176">Plik *runtimeconfig. JSON* to plik konfiguracji zawierający ustawienia czasu wykonywania.</span><span class="sxs-lookup"><span data-stu-id="b9e97-176">A *runtimeconfig.json* file is a configuration file containing run-time settings.</span></span> <span data-ttu-id="b9e97-177">Aby uzyskać więcej informacji, zobacz [Ustawienia konfiguracji środowiska uruchomieniowego .NET Core](../run-time-config/index.md#runtimeconfigjson).</span><span class="sxs-lookup"><span data-stu-id="b9e97-177">For more information, see [.NET Core run-time configuration settings](../run-time-config/index.md#runtimeconfigjson).</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="b9e97-178">Ustawia poziom szczegółowości polecenia.</span><span class="sxs-lookup"><span data-stu-id="b9e97-178">Sets the verbosity level of the command.</span></span> <span data-ttu-id="b9e97-179">Dozwolone wartości to `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`i `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="b9e97-179">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="b9e97-180">Nieobsługiwane w każdym poleceniu; Aby określić, czy ta opcja jest dostępna, zobacz określoną stronę poleceń.</span><span class="sxs-lookup"><span data-stu-id="b9e97-180">Not supported in every command; see specific command page to determine if this option is available.</span></span>

`--version`

<span data-ttu-id="b9e97-181">Drukuje używaną wersję zestaw .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="b9e97-181">Prints out the version of the .NET Core SDK in use.</span></span>

---

## <a name="dotnet-commands"></a><span data-ttu-id="b9e97-182">Polecenia dotnet</span><span class="sxs-lookup"><span data-stu-id="b9e97-182">dotnet commands</span></span>

### <a name="general"></a><span data-ttu-id="b9e97-183">Ogólne</span><span class="sxs-lookup"><span data-stu-id="b9e97-183">General</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="b9e97-184">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="b9e97-184">.NET Core 2.1</span></span>](#tab/netcore21)

| <span data-ttu-id="b9e97-185">Polecenie</span><span class="sxs-lookup"><span data-stu-id="b9e97-185">Command</span></span>                                       | <span data-ttu-id="b9e97-186">Funkcja</span><span class="sxs-lookup"><span data-stu-id="b9e97-186">Function</span></span>                                                            |
| --------------------------------------------- | ------------------------------------------------------------------- |
| [<span data-ttu-id="b9e97-187">dotnet build</span><span class="sxs-lookup"><span data-stu-id="b9e97-187">dotnet build</span></span>](dotnet-build.md)               | <span data-ttu-id="b9e97-188">Kompiluje aplikację platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="b9e97-188">Builds a .NET Core application.</span></span>                                     |
| [<span data-ttu-id="b9e97-189">dotnet build-server</span><span class="sxs-lookup"><span data-stu-id="b9e97-189">dotnet build-server</span></span>](dotnet-build-server.md) | <span data-ttu-id="b9e97-190">Współdziała z serwerami uruchomionymi przez kompilację.</span><span class="sxs-lookup"><span data-stu-id="b9e97-190">Interacts with servers started by a build.</span></span>                          |
| [<span data-ttu-id="b9e97-191">dotnet clean</span><span class="sxs-lookup"><span data-stu-id="b9e97-191">dotnet clean</span></span>](dotnet-clean.md)               | <span data-ttu-id="b9e97-192">Czyste dane wyjściowe kompilacji.</span><span class="sxs-lookup"><span data-stu-id="b9e97-192">Clean build outputs.</span></span>                                                |
| [<span data-ttu-id="b9e97-193">dotnet help</span><span class="sxs-lookup"><span data-stu-id="b9e97-193">dotnet help</span></span>](dotnet-help.md)                 | <span data-ttu-id="b9e97-194">Przedstawia bardziej szczegółową dokumentację dla polecenia w trybie online.</span><span class="sxs-lookup"><span data-stu-id="b9e97-194">Shows more detailed documentation online for the command.</span></span>           |
| [<span data-ttu-id="b9e97-195">dotnet migrate</span><span class="sxs-lookup"><span data-stu-id="b9e97-195">dotnet migrate</span></span>](dotnet-migrate.md)           | <span data-ttu-id="b9e97-196">Migruje prawidłowy projekt w wersji zapoznawczej 2 do projektu zestaw .NET Core SDK 1,0.</span><span class="sxs-lookup"><span data-stu-id="b9e97-196">Migrates a valid Preview 2 project to a .NET Core SDK 1.0 project.</span></span>  |
| [<span data-ttu-id="b9e97-197">dotnet msbuild</span><span class="sxs-lookup"><span data-stu-id="b9e97-197">dotnet msbuild</span></span>](dotnet-msbuild.md)           | <span data-ttu-id="b9e97-198">Zapewnia dostęp do wiersza polecenia programu MSBuild.</span><span class="sxs-lookup"><span data-stu-id="b9e97-198">Provides access to the MSBuild command line.</span></span>                        |
| [<span data-ttu-id="b9e97-199">dotnet new</span><span class="sxs-lookup"><span data-stu-id="b9e97-199">dotnet new</span></span>](dotnet-new.md)                   | <span data-ttu-id="b9e97-200">Inicjuje projekt C# lub F# dla danego szablonu.</span><span class="sxs-lookup"><span data-stu-id="b9e97-200">Initializes a C# or F# project for a given template.</span></span>                |
| [<span data-ttu-id="b9e97-201">dotnet pack</span><span class="sxs-lookup"><span data-stu-id="b9e97-201">dotnet pack</span></span>](dotnet-pack.md)                 | <span data-ttu-id="b9e97-202">Tworzy pakiet NuGet kodu.</span><span class="sxs-lookup"><span data-stu-id="b9e97-202">Creates a NuGet package of your code.</span></span>                               |
| [<span data-ttu-id="b9e97-203">dotnet publish</span><span class="sxs-lookup"><span data-stu-id="b9e97-203">dotnet publish</span></span>](dotnet-publish.md)           | <span data-ttu-id="b9e97-204">Publikuje zależne od programu .NET Framework lub samodzielną aplikację.</span><span class="sxs-lookup"><span data-stu-id="b9e97-204">Publishes a .NET framework-dependent or self-contained application.</span></span> |
| [<span data-ttu-id="b9e97-205">dotnet restore</span><span class="sxs-lookup"><span data-stu-id="b9e97-205">dotnet restore</span></span>](dotnet-restore.md)           | <span data-ttu-id="b9e97-206">Przywraca zależności dla danej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="b9e97-206">Restores the dependencies for a given application.</span></span>                  |
| [<span data-ttu-id="b9e97-207">dotnet run</span><span class="sxs-lookup"><span data-stu-id="b9e97-207">dotnet run</span></span>](dotnet-run.md)                   | <span data-ttu-id="b9e97-208">Uruchamia aplikację ze źródła.</span><span class="sxs-lookup"><span data-stu-id="b9e97-208">Runs the application from source.</span></span>                                   |
| [<span data-ttu-id="b9e97-209">dotnet sln</span><span class="sxs-lookup"><span data-stu-id="b9e97-209">dotnet sln</span></span>](dotnet-sln.md)                   | <span data-ttu-id="b9e97-210">Opcje dodawania, usuwania i wyświetlania listy projektów w pliku rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="b9e97-210">Options to add, remove, and list projects in a solution file.</span></span>       |
| [<span data-ttu-id="b9e97-211">dotnet store</span><span class="sxs-lookup"><span data-stu-id="b9e97-211">dotnet store</span></span>](dotnet-store.md)               | <span data-ttu-id="b9e97-212">Przechowuje zestawy w magazynie pakietów środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="b9e97-212">Stores assemblies in the runtime package store.</span></span>                     |
| [<span data-ttu-id="b9e97-213">dotnet test</span><span class="sxs-lookup"><span data-stu-id="b9e97-213">dotnet test</span></span>](dotnet-test.md)                 | <span data-ttu-id="b9e97-214">Uruchamia testy przy użyciu modułu uruchamiającego testy.</span><span class="sxs-lookup"><span data-stu-id="b9e97-214">Runs tests using a test runner.</span></span>                                     |

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="b9e97-215">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="b9e97-215">.NET Core 2.0</span></span>](#tab/netcore20)

| <span data-ttu-id="b9e97-216">Polecenie</span><span class="sxs-lookup"><span data-stu-id="b9e97-216">Command</span></span>                             | <span data-ttu-id="b9e97-217">Funkcja</span><span class="sxs-lookup"><span data-stu-id="b9e97-217">Function</span></span>                                                            |
| ----------------------------------- | ------------------------------------------------------------------- |
| [<span data-ttu-id="b9e97-218">dotnet build</span><span class="sxs-lookup"><span data-stu-id="b9e97-218">dotnet build</span></span>](dotnet-build.md)     | <span data-ttu-id="b9e97-219">Kompiluje aplikację platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="b9e97-219">Builds a .NET Core application.</span></span>                                     |
| [<span data-ttu-id="b9e97-220">dotnet clean</span><span class="sxs-lookup"><span data-stu-id="b9e97-220">dotnet clean</span></span>](dotnet-clean.md)     | <span data-ttu-id="b9e97-221">Czyste dane wyjściowe kompilacji.</span><span class="sxs-lookup"><span data-stu-id="b9e97-221">Clean build outputs.</span></span>                                              |
| [<span data-ttu-id="b9e97-222">dotnet help</span><span class="sxs-lookup"><span data-stu-id="b9e97-222">dotnet help</span></span>](dotnet-help.md)       | <span data-ttu-id="b9e97-223">Przedstawia bardziej szczegółową dokumentację dla polecenia w trybie online.</span><span class="sxs-lookup"><span data-stu-id="b9e97-223">Shows more detailed documentation online for the command.</span></span>           |
| [<span data-ttu-id="b9e97-224">dotnet migrate</span><span class="sxs-lookup"><span data-stu-id="b9e97-224">dotnet migrate</span></span>](dotnet-migrate.md) | <span data-ttu-id="b9e97-225">Migruje prawidłowy projekt w wersji zapoznawczej 2 do projektu zestaw .NET Core SDK 1,0.</span><span class="sxs-lookup"><span data-stu-id="b9e97-225">Migrates a valid Preview 2 project to a .NET Core SDK 1.0 project.</span></span>  |
| [<span data-ttu-id="b9e97-226">dotnet msbuild</span><span class="sxs-lookup"><span data-stu-id="b9e97-226">dotnet msbuild</span></span>](dotnet-msbuild.md) | <span data-ttu-id="b9e97-227">Zapewnia dostęp do wiersza polecenia programu MSBuild.</span><span class="sxs-lookup"><span data-stu-id="b9e97-227">Provides access to the MSBuild command line.</span></span>                        |
| [<span data-ttu-id="b9e97-228">dotnet new</span><span class="sxs-lookup"><span data-stu-id="b9e97-228">dotnet new</span></span>](dotnet-new.md)         | <span data-ttu-id="b9e97-229">Inicjuje projekt C# lub F# dla danego szablonu.</span><span class="sxs-lookup"><span data-stu-id="b9e97-229">Initializes a C# or F# project for a given template.</span></span>                |
| [<span data-ttu-id="b9e97-230">dotnet pack</span><span class="sxs-lookup"><span data-stu-id="b9e97-230">dotnet pack</span></span>](dotnet-pack.md)       | <span data-ttu-id="b9e97-231">Tworzy pakiet NuGet kodu.</span><span class="sxs-lookup"><span data-stu-id="b9e97-231">Creates a NuGet package of your code.</span></span>                               |
| [<span data-ttu-id="b9e97-232">dotnet publish</span><span class="sxs-lookup"><span data-stu-id="b9e97-232">dotnet publish</span></span>](dotnet-publish.md) | <span data-ttu-id="b9e97-233">Publikuje zależne od programu .NET Framework lub samodzielną aplikację.</span><span class="sxs-lookup"><span data-stu-id="b9e97-233">Publishes a .NET framework-dependent or self-contained application.</span></span> |
| [<span data-ttu-id="b9e97-234">dotnet restore</span><span class="sxs-lookup"><span data-stu-id="b9e97-234">dotnet restore</span></span>](dotnet-restore.md) | <span data-ttu-id="b9e97-235">Przywraca zależności dla danej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="b9e97-235">Restores the dependencies for a given application.</span></span>                  |
| [<span data-ttu-id="b9e97-236">dotnet run</span><span class="sxs-lookup"><span data-stu-id="b9e97-236">dotnet run</span></span>](dotnet-run.md)         | <span data-ttu-id="b9e97-237">Uruchamia aplikację ze źródła.</span><span class="sxs-lookup"><span data-stu-id="b9e97-237">Runs the application from source.</span></span>                                   |
| [<span data-ttu-id="b9e97-238">dotnet sln</span><span class="sxs-lookup"><span data-stu-id="b9e97-238">dotnet sln</span></span>](dotnet-sln.md)         | <span data-ttu-id="b9e97-239">Opcje dodawania, usuwania i wyświetlania listy projektów w pliku rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="b9e97-239">Options to add, remove, and list projects in a solution file.</span></span>       |
| [<span data-ttu-id="b9e97-240">dotnet store</span><span class="sxs-lookup"><span data-stu-id="b9e97-240">dotnet store</span></span>](dotnet-store.md)     | <span data-ttu-id="b9e97-241">Przechowuje zestawy w magazynie pakietów środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="b9e97-241">Stores assemblies in the runtime package store.</span></span>                     |
| [<span data-ttu-id="b9e97-242">dotnet test</span><span class="sxs-lookup"><span data-stu-id="b9e97-242">dotnet test</span></span>](dotnet-test.md)       | <span data-ttu-id="b9e97-243">Uruchamia testy przy użyciu modułu uruchamiającego testy.</span><span class="sxs-lookup"><span data-stu-id="b9e97-243">Runs tests using a test runner.</span></span>                                     |

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="b9e97-244">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="b9e97-244">.NET Core 1.x</span></span>](#tab/netcore1x)

| <span data-ttu-id="b9e97-245">Polecenie</span><span class="sxs-lookup"><span data-stu-id="b9e97-245">Command</span></span>                             | <span data-ttu-id="b9e97-246">Funkcja</span><span class="sxs-lookup"><span data-stu-id="b9e97-246">Function</span></span>                                                            |
| ----------------------------------- | ------------------------------------------------------------------- |
| [<span data-ttu-id="b9e97-247">dotnet build</span><span class="sxs-lookup"><span data-stu-id="b9e97-247">dotnet build</span></span>](dotnet-build.md)     | <span data-ttu-id="b9e97-248">Kompiluje aplikację platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="b9e97-248">Builds a .NET Core application.</span></span>                                     |
| [<span data-ttu-id="b9e97-249">dotnet clean</span><span class="sxs-lookup"><span data-stu-id="b9e97-249">dotnet clean</span></span>](dotnet-clean.md)     | <span data-ttu-id="b9e97-250">Czyste dane wyjściowe kompilacji.</span><span class="sxs-lookup"><span data-stu-id="b9e97-250">Clean build outputs.</span></span>                                              |
| [<span data-ttu-id="b9e97-251">dotnet migrate</span><span class="sxs-lookup"><span data-stu-id="b9e97-251">dotnet migrate</span></span>](dotnet-migrate.md) | <span data-ttu-id="b9e97-252">Migruje prawidłowy projekt w wersji zapoznawczej 2 do projektu zestaw .NET Core SDK 1,0.</span><span class="sxs-lookup"><span data-stu-id="b9e97-252">Migrates a valid Preview 2 project to a .NET Core SDK 1.0 project.</span></span>  |
| [<span data-ttu-id="b9e97-253">dotnet msbuild</span><span class="sxs-lookup"><span data-stu-id="b9e97-253">dotnet msbuild</span></span>](dotnet-msbuild.md) | <span data-ttu-id="b9e97-254">Zapewnia dostęp do wiersza polecenia programu MSBuild.</span><span class="sxs-lookup"><span data-stu-id="b9e97-254">Provides access to the MSBuild command line.</span></span>                        |
| [<span data-ttu-id="b9e97-255">dotnet new</span><span class="sxs-lookup"><span data-stu-id="b9e97-255">dotnet new</span></span>](dotnet-new.md)         | <span data-ttu-id="b9e97-256">Inicjuje projekt C# lub F# dla danego szablonu.</span><span class="sxs-lookup"><span data-stu-id="b9e97-256">Initializes a C# or F# project for a given template.</span></span>                |
| [<span data-ttu-id="b9e97-257">dotnet pack</span><span class="sxs-lookup"><span data-stu-id="b9e97-257">dotnet pack</span></span>](dotnet-pack.md)       | <span data-ttu-id="b9e97-258">Tworzy pakiet NuGet kodu.</span><span class="sxs-lookup"><span data-stu-id="b9e97-258">Creates a NuGet package of your code.</span></span>                               |
| [<span data-ttu-id="b9e97-259">dotnet publish</span><span class="sxs-lookup"><span data-stu-id="b9e97-259">dotnet publish</span></span>](dotnet-publish.md) | <span data-ttu-id="b9e97-260">Publikuje zależne od programu .NET Framework lub samodzielną aplikację.</span><span class="sxs-lookup"><span data-stu-id="b9e97-260">Publishes a .NET framework-dependent or self-contained application.</span></span> |
| [<span data-ttu-id="b9e97-261">dotnet restore</span><span class="sxs-lookup"><span data-stu-id="b9e97-261">dotnet restore</span></span>](dotnet-restore.md) | <span data-ttu-id="b9e97-262">Przywraca zależności dla danej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="b9e97-262">Restores the dependencies for a given application.</span></span>                  |
| [<span data-ttu-id="b9e97-263">dotnet run</span><span class="sxs-lookup"><span data-stu-id="b9e97-263">dotnet run</span></span>](dotnet-run.md)         | <span data-ttu-id="b9e97-264">Uruchamia aplikację ze źródła.</span><span class="sxs-lookup"><span data-stu-id="b9e97-264">Runs the application from source.</span></span>                                   |
| [<span data-ttu-id="b9e97-265">dotnet sln</span><span class="sxs-lookup"><span data-stu-id="b9e97-265">dotnet sln</span></span>](dotnet-sln.md)         | <span data-ttu-id="b9e97-266">Opcje dodawania, usuwania i wyświetlania listy projektów w pliku rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="b9e97-266">Options to add, remove, and list projects in a solution file.</span></span>       |
| [<span data-ttu-id="b9e97-267">dotnet test</span><span class="sxs-lookup"><span data-stu-id="b9e97-267">dotnet test</span></span>](dotnet-test.md)       | <span data-ttu-id="b9e97-268">Uruchamia testy przy użyciu modułu uruchamiającego testy.</span><span class="sxs-lookup"><span data-stu-id="b9e97-268">Runs tests using a test runner.</span></span>                                     |

---

### <a name="project-references"></a><span data-ttu-id="b9e97-269">Odwołania projektu</span><span class="sxs-lookup"><span data-stu-id="b9e97-269">Project references</span></span>

<span data-ttu-id="b9e97-270">Polecenie</span><span class="sxs-lookup"><span data-stu-id="b9e97-270">Command</span></span> | <span data-ttu-id="b9e97-271">Funkcja</span><span class="sxs-lookup"><span data-stu-id="b9e97-271">Function</span></span>
--- | ---
[<span data-ttu-id="b9e97-272">dotnet add reference</span><span class="sxs-lookup"><span data-stu-id="b9e97-272">dotnet add reference</span></span>](dotnet-add-reference.md) | <span data-ttu-id="b9e97-273">Dodaje odwołanie do projektu.</span><span class="sxs-lookup"><span data-stu-id="b9e97-273">Adds a project reference.</span></span>
[<span data-ttu-id="b9e97-274">dotnet list reference</span><span class="sxs-lookup"><span data-stu-id="b9e97-274">dotnet list reference</span></span>](dotnet-list-reference.md) | <span data-ttu-id="b9e97-275">Wyświetla listę odwołań do projektu.</span><span class="sxs-lookup"><span data-stu-id="b9e97-275">Lists project references.</span></span>
[<span data-ttu-id="b9e97-276">dotnet remove reference</span><span class="sxs-lookup"><span data-stu-id="b9e97-276">dotnet remove reference</span></span>](dotnet-remove-reference.md) | <span data-ttu-id="b9e97-277">Usuwa odwołanie do projektu.</span><span class="sxs-lookup"><span data-stu-id="b9e97-277">Removes a project reference.</span></span>

### <a name="nuget-packages"></a><span data-ttu-id="b9e97-278">Pakiety NuGet</span><span class="sxs-lookup"><span data-stu-id="b9e97-278">NuGet packages</span></span>

<span data-ttu-id="b9e97-279">Polecenie</span><span class="sxs-lookup"><span data-stu-id="b9e97-279">Command</span></span> | <span data-ttu-id="b9e97-280">Funkcja</span><span class="sxs-lookup"><span data-stu-id="b9e97-280">Function</span></span>
--- | ---
[<span data-ttu-id="b9e97-281">dotnet add package</span><span class="sxs-lookup"><span data-stu-id="b9e97-281">dotnet add package</span></span>](dotnet-add-package.md) | <span data-ttu-id="b9e97-282">Dodaje pakiet NuGet.</span><span class="sxs-lookup"><span data-stu-id="b9e97-282">Adds a NuGet package.</span></span>
[<span data-ttu-id="b9e97-283">dotnet remove package</span><span class="sxs-lookup"><span data-stu-id="b9e97-283">dotnet remove package</span></span>](dotnet-remove-package.md) | <span data-ttu-id="b9e97-284">Usuwa pakiet NuGet.</span><span class="sxs-lookup"><span data-stu-id="b9e97-284">Removes a NuGet package.</span></span>

### <a name="nuget-commands"></a><span data-ttu-id="b9e97-285">Polecenia NuGet</span><span class="sxs-lookup"><span data-stu-id="b9e97-285">NuGet commands</span></span>

<span data-ttu-id="b9e97-286">Polecenie</span><span class="sxs-lookup"><span data-stu-id="b9e97-286">Command</span></span> | <span data-ttu-id="b9e97-287">Funkcja</span><span class="sxs-lookup"><span data-stu-id="b9e97-287">Function</span></span>
--- | ---
[<span data-ttu-id="b9e97-288">dotnet nuget delete</span><span class="sxs-lookup"><span data-stu-id="b9e97-288">dotnet nuget delete</span></span>](dotnet-nuget-delete.md) | <span data-ttu-id="b9e97-289">Usuwa pakiet z serwera lub go wystawia.</span><span class="sxs-lookup"><span data-stu-id="b9e97-289">Deletes or unlists a package from the server.</span></span>
[<span data-ttu-id="b9e97-290">dotnet nuget locals</span><span class="sxs-lookup"><span data-stu-id="b9e97-290">dotnet nuget locals</span></span>](dotnet-nuget-locals.md) | <span data-ttu-id="b9e97-291">Czyści lub wyświetla lokalne zasoby NuGet, takie jak pamięć podręczna żądań HTTP, tymczasowa pamięć podręczna lub folder pakietów globalnych dla całego komputera.</span><span class="sxs-lookup"><span data-stu-id="b9e97-291">Clears or lists local NuGet resources such as http-request cache, temporary cache, or machine-wide global packages folder.</span></span>
[<span data-ttu-id="b9e97-292">dotnet nuget push</span><span class="sxs-lookup"><span data-stu-id="b9e97-292">dotnet nuget push</span></span>](dotnet-nuget-push.md) | <span data-ttu-id="b9e97-293">Wypchnij pakiet na serwer i opublikuje go.</span><span class="sxs-lookup"><span data-stu-id="b9e97-293">Pushes a package to the server and publishes it.</span></span>

### <a name="global-tools-commands"></a><span data-ttu-id="b9e97-294">Polecenia narzędzi globalnych</span><span class="sxs-lookup"><span data-stu-id="b9e97-294">Global Tools commands</span></span>

<span data-ttu-id="b9e97-295">[Narzędzia globalne platformy .NET Core](global-tools.md) są dostępne począwszy od zestaw .NET Core SDK 2.1.300:</span><span class="sxs-lookup"><span data-stu-id="b9e97-295">[.NET Core Global Tools](global-tools.md) are available starting with .NET Core SDK 2.1.300:</span></span>

<span data-ttu-id="b9e97-296">Polecenie</span><span class="sxs-lookup"><span data-stu-id="b9e97-296">Command</span></span> | <span data-ttu-id="b9e97-297">Funkcja</span><span class="sxs-lookup"><span data-stu-id="b9e97-297">Function</span></span>
--- | ---
[<span data-ttu-id="b9e97-298">dotnet tool install</span><span class="sxs-lookup"><span data-stu-id="b9e97-298">dotnet tool install</span></span>](dotnet-tool-install.md) | <span data-ttu-id="b9e97-299">Instaluje narzędzie globalne na komputerze.</span><span class="sxs-lookup"><span data-stu-id="b9e97-299">Installs a Global Tool on your machine.</span></span>
[<span data-ttu-id="b9e97-300">dotnet tool list</span><span class="sxs-lookup"><span data-stu-id="b9e97-300">dotnet tool list</span></span>](dotnet-tool-list.md) | <span data-ttu-id="b9e97-301">Wyświetla listę wszystkich narzędzi globalnych aktualnie zainstalowanych w domyślnym katalogu na komputerze lub w określonej ścieżce.</span><span class="sxs-lookup"><span data-stu-id="b9e97-301">Lists all Global Tools currently installed in the default directory on your machine or in the specified path.</span></span>
[<span data-ttu-id="b9e97-302">dotnet tool uninstall</span><span class="sxs-lookup"><span data-stu-id="b9e97-302">dotnet tool uninstall</span></span>](dotnet-tool-uninstall.md) | <span data-ttu-id="b9e97-303">Odinstalowuje narzędzie globalne z komputera.</span><span class="sxs-lookup"><span data-stu-id="b9e97-303">Uninstalls a Global Tool from your machine.</span></span>
[<span data-ttu-id="b9e97-304">dotnet tool update</span><span class="sxs-lookup"><span data-stu-id="b9e97-304">dotnet tool update</span></span>](dotnet-tool-update.md) | <span data-ttu-id="b9e97-305">Aktualizuje narzędzie globalne na komputerze.</span><span class="sxs-lookup"><span data-stu-id="b9e97-305">Updates a Global Tool on your machine.</span></span>

### <a name="additional-tools"></a><span data-ttu-id="b9e97-306">Dodatkowe narzędzia</span><span class="sxs-lookup"><span data-stu-id="b9e97-306">Additional tools</span></span>

<span data-ttu-id="b9e97-307">Począwszy od zestaw .NET Core SDK 2.1.300, wiele narzędzi, które były dostępne tylko dla poszczególnych projektów, przy użyciu `DotnetCliToolReference`, są teraz dostępne jako część zestaw .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="b9e97-307">Starting with .NET Core SDK 2.1.300, a number of tools that were available only on a per project basis using `DotnetCliToolReference` are now available as part of the .NET Core SDK.</span></span> <span data-ttu-id="b9e97-308">Te narzędzia są wymienione w poniższej tabeli:</span><span class="sxs-lookup"><span data-stu-id="b9e97-308">These tools are listed in the following table:</span></span>

| <span data-ttu-id="b9e97-309">Narzędzie</span><span class="sxs-lookup"><span data-stu-id="b9e97-309">Tool</span></span>                                              | <span data-ttu-id="b9e97-310">Funkcja</span><span class="sxs-lookup"><span data-stu-id="b9e97-310">Function</span></span>                                                     |
| ------------------------------------------------- | ------------------------------------------------------------ |
| <span data-ttu-id="b9e97-311">dev-certs</span><span class="sxs-lookup"><span data-stu-id="b9e97-311">dev-certs</span></span>                                         | <span data-ttu-id="b9e97-312">Tworzy i zarządza certyfikatami deweloperskimi.</span><span class="sxs-lookup"><span data-stu-id="b9e97-312">Creates and manages development certificates.</span></span>                |
| [<span data-ttu-id="b9e97-313">bieżąco</span><span class="sxs-lookup"><span data-stu-id="b9e97-313">ef</span></span>](/ef/core/miscellaneous/cli/dotnet)           | <span data-ttu-id="b9e97-314">Entity Framework Core narzędzia wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="b9e97-314">Entity Framework Core command-line tools.</span></span>                    |
| <span data-ttu-id="b9e97-315">SQL-pamięć podręczna</span><span class="sxs-lookup"><span data-stu-id="b9e97-315">sql-cache</span></span>                                         | <span data-ttu-id="b9e97-316">SQL Server narzędzia wiersza polecenia pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="b9e97-316">SQL Server cache command-line tools.</span></span>                         |
| [<span data-ttu-id="b9e97-317">wpisy tajne użytkownika</span><span class="sxs-lookup"><span data-stu-id="b9e97-317">user-secrets</span></span>](/aspnet/core/security/app-secrets) | <span data-ttu-id="b9e97-318">Zarządza kluczami tajnymi użytkowników deweloperskich.</span><span class="sxs-lookup"><span data-stu-id="b9e97-318">Manages development user secrets.</span></span>                            |
| [<span data-ttu-id="b9e97-319">Obejrzyj</span><span class="sxs-lookup"><span data-stu-id="b9e97-319">watch</span></span>](/aspnet/core/tutorials/dotnet-watch)      | <span data-ttu-id="b9e97-320">Uruchamia obserwatora plików, który uruchamia polecenie, gdy pliki zmienią się.</span><span class="sxs-lookup"><span data-stu-id="b9e97-320">Starts a file watcher that runs a command when files change.</span></span> |

<span data-ttu-id="b9e97-321">Aby uzyskać więcej informacji na temat każdego narzędzia, wpisz `dotnet <tool-name> --help`.</span><span class="sxs-lookup"><span data-stu-id="b9e97-321">For more information about each tool, type `dotnet <tool-name> --help`.</span></span>

## <a name="examples"></a><span data-ttu-id="b9e97-322">Przykłady</span><span class="sxs-lookup"><span data-stu-id="b9e97-322">Examples</span></span>

<span data-ttu-id="b9e97-323">Tworzy nową aplikację konsolową platformy .NET Core:</span><span class="sxs-lookup"><span data-stu-id="b9e97-323">Creates a new .NET Core console application:</span></span>

`dotnet new console`

<span data-ttu-id="b9e97-324">Przywróć zależności dla danej aplikacji:</span><span class="sxs-lookup"><span data-stu-id="b9e97-324">Restore dependencies for a given application:</span></span>

`dotnet restore`

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

<span data-ttu-id="b9e97-325">Kompiluj projekt i jego zależności w danym katalogu:</span><span class="sxs-lookup"><span data-stu-id="b9e97-325">Build a project and its dependencies in a given directory:</span></span>

`dotnet build`

<span data-ttu-id="b9e97-326">Uruchom bibliotekę DLL aplikacji, taką jak `myapp.dll`:</span><span class="sxs-lookup"><span data-stu-id="b9e97-326">Run an application DLL, such as `myapp.dll`:</span></span>

`dotnet myapp.dll`

## <a name="environment-variables"></a><span data-ttu-id="b9e97-327">Zmienne środowiskowe</span><span class="sxs-lookup"><span data-stu-id="b9e97-327">Environment variables</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="b9e97-328">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="b9e97-328">.NET Core 2.1</span></span>](#tab/netcore21)

`DOTNET_PACKAGES`

<span data-ttu-id="b9e97-329">Folder pakiety globalne.</span><span class="sxs-lookup"><span data-stu-id="b9e97-329">The global packages folder.</span></span> <span data-ttu-id="b9e97-330">Jeśli nie zostanie ustawiona, domyślnie jest `~/.nuget/packages` w systemie UNIX lub `%userprofile%\.nuget\packages` na komputerze z systemem Windows.</span><span class="sxs-lookup"><span data-stu-id="b9e97-330">If not set, it defaults to `~/.nuget/packages` on Unix or `%userprofile%\.nuget\packages` on Windows.</span></span>

`DOTNET_SERVICING`

<span data-ttu-id="b9e97-331">Określa lokalizację indeksu obsługi, który ma być używany przez host udostępniony podczas ładowania środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="b9e97-331">Specifies the location of the servicing index to use by the shared host when loading the runtime.</span></span>

`DOTNET_CLI_TELEMETRY_OPTOUT`

<span data-ttu-id="b9e97-332">Określa, czy dane dotyczące użycia narzędzi .NET Core są zbierane i wysyłane do firmy Microsoft.</span><span class="sxs-lookup"><span data-stu-id="b9e97-332">Specifies whether data about the .NET Core tools usage is collected and sent to Microsoft.</span></span> <span data-ttu-id="b9e97-333">Ustaw `true`, aby zrezygnować z funkcji telemetrii (wartości `true`, `1`lub `yes` zaakceptowane).</span><span class="sxs-lookup"><span data-stu-id="b9e97-333">Set to `true` to opt-out of the telemetry feature (values `true`, `1`, or `yes` accepted).</span></span> <span data-ttu-id="b9e97-334">W przeciwnym razie ustaw wartość `false`, aby zrezygnować z funkcji telemetrii (wartości `false`, `0`lub `no` zaakceptowane).</span><span class="sxs-lookup"><span data-stu-id="b9e97-334">Otherwise, set to `false` to opt into the telemetry features (values `false`, `0`, or `no` accepted).</span></span> <span data-ttu-id="b9e97-335">Jeśli nie zostanie ustawiona, wartość domyślna to `false` i aktywna jest funkcja telemetrii.</span><span class="sxs-lookup"><span data-stu-id="b9e97-335">If not set, the default is `false` and the telemetry feature is active.</span></span>

`DOTNET_MULTILEVEL_LOOKUP`

<span data-ttu-id="b9e97-336">Określa, czy środowisko uruchomieniowe programu .NET Core, udostępnione środowisko lub zestaw SDK są rozpoznawane z lokalizacji globalnej.</span><span class="sxs-lookup"><span data-stu-id="b9e97-336">Specifies whether .NET Core runtime, shared framework, or SDK are resolved from the global location.</span></span> <span data-ttu-id="b9e97-337">Jeśli nie zostanie ustawiona, domyślnie `true`.</span><span class="sxs-lookup"><span data-stu-id="b9e97-337">If not set, it defaults to `true`.</span></span> <span data-ttu-id="b9e97-338">Ustaw `false`, aby nie rozwiązany z lokalizacji globalnej i mieć izolowane instalacje platformy .NET Core (wartości `0` lub `false` są akceptowane).</span><span class="sxs-lookup"><span data-stu-id="b9e97-338">Set to `false` to not resolve from the global location and have isolated .NET Core installations (values `0` or `false` are accepted).</span></span> <span data-ttu-id="b9e97-339">Aby uzyskać więcej informacji o wyszukiwaniu wielu poziomów, zobacz [SharedFX wyszukiwanie na wielu poziomach](https://github.com/dotnet/core-setup/blob/master/Documentation/design-docs/multilevel-sharedfx-lookup.md).</span><span class="sxs-lookup"><span data-stu-id="b9e97-339">For more information about multi-level lookup, see [Multi-level SharedFX Lookup](https://github.com/dotnet/core-setup/blob/master/Documentation/design-docs/multilevel-sharedfx-lookup.md).</span></span>

`DOTNET_ROLL_FORWARD_ON_NO_CANDIDATE_FX`

<span data-ttu-id="b9e97-340">Wyłącza opcję wycofywania wersji pomocniczej, jeśli jest ustawiona na `0`.</span><span class="sxs-lookup"><span data-stu-id="b9e97-340">Disables minor version roll forward, if set to `0`.</span></span> <span data-ttu-id="b9e97-341">Aby uzyskać więcej informacji, zobacz [przewinięcie do przodu](../whats-new/dotnet-core-2-1.md#roll-forward).</span><span class="sxs-lookup"><span data-stu-id="b9e97-341">For more information, see [Roll forward](../whats-new/dotnet-core-2-1.md#roll-forward).</span></span>

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="b9e97-342">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="b9e97-342">.NET Core 2.0</span></span>](#tab/netcore20)

`DOTNET_PACKAGES`

<span data-ttu-id="b9e97-343">Podstawowa pamięć podręczna pakietu.</span><span class="sxs-lookup"><span data-stu-id="b9e97-343">The primary package cache.</span></span> <span data-ttu-id="b9e97-344">Jeśli nie zostanie ustawiona, domyślnie jest `$HOME/.nuget/packages` w systemie UNIX lub `%userprofile%\.nuget\packages` na komputerze z systemem Windows.</span><span class="sxs-lookup"><span data-stu-id="b9e97-344">If not set, it defaults to `$HOME/.nuget/packages` on Unix or `%userprofile%\.nuget\packages` on Windows.</span></span>

`DOTNET_SERVICING`

<span data-ttu-id="b9e97-345">Określa lokalizację indeksu obsługi, który ma być używany przez host udostępniony podczas ładowania środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="b9e97-345">Specifies the location of the servicing index to use by the shared host when loading the runtime.</span></span>

`DOTNET_CLI_TELEMETRY_OPTOUT`

<span data-ttu-id="b9e97-346">Określa, czy dane dotyczące użycia narzędzi .NET Core są zbierane i wysyłane do firmy Microsoft.</span><span class="sxs-lookup"><span data-stu-id="b9e97-346">Specifies whether data about the .NET Core tools usage is collected and sent to Microsoft.</span></span> <span data-ttu-id="b9e97-347">Ustaw `true`, aby zrezygnować z funkcji telemetrii (wartości `true`, `1`lub `yes` zaakceptowane).</span><span class="sxs-lookup"><span data-stu-id="b9e97-347">Set to `true` to opt-out of the telemetry feature (values `true`, `1`, or `yes` accepted).</span></span> <span data-ttu-id="b9e97-348">W przeciwnym razie ustaw wartość `false`, aby zrezygnować z funkcji telemetrii (wartości `false`, `0`lub `no` zaakceptowane).</span><span class="sxs-lookup"><span data-stu-id="b9e97-348">Otherwise, set to `false` to opt into the telemetry features (values `false`, `0`, or `no` accepted).</span></span> <span data-ttu-id="b9e97-349">Jeśli nie zostanie ustawiona, wartość domyślna to `false` i aktywna jest funkcja telemetrii.</span><span class="sxs-lookup"><span data-stu-id="b9e97-349">If not set, the default is `false` and the telemetry feature is active.</span></span>

`DOTNET_MULTILEVEL_LOOKUP`

<span data-ttu-id="b9e97-350">Określa, czy środowisko uruchomieniowe programu .NET Core, udostępnione środowisko lub zestaw SDK są rozpoznawane z lokalizacji globalnej.</span><span class="sxs-lookup"><span data-stu-id="b9e97-350">Specifies whether .NET Core runtime, shared framework, or SDK are resolved from the global location.</span></span> <span data-ttu-id="b9e97-351">Jeśli nie zostanie ustawiona, domyślnie `true`.</span><span class="sxs-lookup"><span data-stu-id="b9e97-351">If not set, it defaults to `true`.</span></span> <span data-ttu-id="b9e97-352">Ustaw `false`, aby nie rozwiązany z lokalizacji globalnej i mieć izolowane instalacje platformy .NET Core (wartości `0` lub `false` są akceptowane).</span><span class="sxs-lookup"><span data-stu-id="b9e97-352">Set to `false` to not resolve from the global location and have isolated .NET Core installations (values `0` or `false` are accepted).</span></span> <span data-ttu-id="b9e97-353">Aby uzyskać więcej informacji o wyszukiwaniu wielu poziomów, zobacz [SharedFX wyszukiwanie na wielu poziomach](https://github.com/dotnet/core-setup/blob/master/Documentation/design-docs/multilevel-sharedfx-lookup.md).</span><span class="sxs-lookup"><span data-stu-id="b9e97-353">For more information about multi-level lookup, see [Multi-level SharedFX Lookup](https://github.com/dotnet/core-setup/blob/master/Documentation/design-docs/multilevel-sharedfx-lookup.md).</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="b9e97-354">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="b9e97-354">.NET Core 1.x</span></span>](#tab/netcore1x)

`DOTNET_PACKAGES`

<span data-ttu-id="b9e97-355">Podstawowa pamięć podręczna pakietu.</span><span class="sxs-lookup"><span data-stu-id="b9e97-355">The primary package cache.</span></span> <span data-ttu-id="b9e97-356">Jeśli nie zostanie ustawiona, domyślnie jest `$HOME/.nuget/packages` w systemie UNIX lub `%userprofile%\.nuget\packages` na komputerze z systemem Windows.</span><span class="sxs-lookup"><span data-stu-id="b9e97-356">If not set, it defaults to `$HOME/.nuget/packages` on Unix or `%userprofile%\.nuget\packages` on Windows.</span></span>

`DOTNET_SERVICING`

<span data-ttu-id="b9e97-357">Określa lokalizację indeksu obsługi, który ma być używany przez host udostępniony podczas ładowania środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="b9e97-357">Specifies the location of the servicing index to use by the shared host when loading the runtime.</span></span>

`DOTNET_CLI_TELEMETRY_OPTOUT`

<span data-ttu-id="b9e97-358">Określa, czy dane dotyczące użycia narzędzi .NET Core są zbierane i wysyłane do firmy Microsoft.</span><span class="sxs-lookup"><span data-stu-id="b9e97-358">Specifies whether data about the .NET Core tools usage is collected and sent to Microsoft.</span></span> <span data-ttu-id="b9e97-359">Ustaw `true`, aby zrezygnować z funkcji telemetrii (wartości `true`, `1`lub `yes` zaakceptowane).</span><span class="sxs-lookup"><span data-stu-id="b9e97-359">Set to `true` to opt-out of the telemetry feature (values `true`, `1`, or `yes` accepted).</span></span> <span data-ttu-id="b9e97-360">W przeciwnym razie ustaw wartość `false`, aby zrezygnować z funkcji telemetrii (wartości `false`, `0`lub `no` zaakceptowane).</span><span class="sxs-lookup"><span data-stu-id="b9e97-360">Otherwise, set to `false` to opt into the telemetry features (values `false`, `0`, or `no` accepted).</span></span> <span data-ttu-id="b9e97-361">Jeśli nie zostanie ustawiona, wartość domyślna to `false` i aktywna jest funkcja telemetrii.</span><span class="sxs-lookup"><span data-stu-id="b9e97-361">If not set, the default is `false` and the telemetry feature is active.</span></span>

---

## <a name="see-also"></a><span data-ttu-id="b9e97-362">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b9e97-362">See also</span></span>

- [<span data-ttu-id="b9e97-363">Pliki konfiguracji środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="b9e97-363">Runtime Configuration Files</span></span>](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md)
- [<span data-ttu-id="b9e97-364">Ustawienia konfiguracji środowiska uruchomieniowego .NET Core</span><span class="sxs-lookup"><span data-stu-id="b9e97-364">.NET Core run-time configuration settings</span></span>](../run-time-config/index.md)
