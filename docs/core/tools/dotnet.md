---
title: dotnet — polecenie
description: Dowiedz się więcej na temat polecenia dotnet (sterownika generycznego dla interfejs wiersza polecenia platformy .NET Core) i jego użycia.
ms.date: 02/13/2020
ms.openlocfilehash: 364978465b63401907b46ead64dbceb2f15c8169
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/19/2020
ms.locfileid: "77451171"
---
# <a name="dotnet-command"></a><span data-ttu-id="17a85-103">dotnet — polecenie</span><span class="sxs-lookup"><span data-stu-id="17a85-103">dotnet command</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="17a85-104">Name (Nazwa)</span><span class="sxs-lookup"><span data-stu-id="17a85-104">Name</span></span>

<span data-ttu-id="17a85-105">`dotnet` — narzędzie do zarządzania kodem źródłowym i plikami binarnymi platformy .NET.</span><span class="sxs-lookup"><span data-stu-id="17a85-105">`dotnet` - A tool for managing .NET source code and binaries.</span></span>

## <a name="synopsis"></a><span data-ttu-id="17a85-106">Streszczenie</span><span class="sxs-lookup"><span data-stu-id="17a85-106">Synopsis</span></span>

<!-- markdownlint-disable MD025 -->

# <a name="net-core-21"></a>[<span data-ttu-id="17a85-107">.NET Core 2,1</span><span class="sxs-lookup"><span data-stu-id="17a85-107">.NET Core 2.1</span></span>](#tab/netcore21)

```dotnetcli
dotnet [command] [arguments] [--additional-deps] [--additionalprobingpath] [--depsfile]
    [-d|--diagnostics] [--fx-version] [-h|--help] [--info] [--list-runtimes] [--list-sdks] [--roll-forward-on-no-candidate-fx] [--runtimeconfig] [-v|--verbosity] [--version]
```

# <a name="net-core-20"></a>[<span data-ttu-id="17a85-108">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="17a85-108">.NET Core 2.0</span></span>](#tab/netcore20)

```dotnetcli
dotnet [command] [arguments] [--additional-deps] [--additionalprobingpath] [--depsfile]
    [-d|--diagnostics] [--fx-version] [-h|--help] [--info] [--roll-forward-on-no-candidate-fx]
    [--runtimeconfig] [-v|--verbosity] [--version]
```

# <a name="net-core-1x"></a>[<span data-ttu-id="17a85-109">.NET Core 1. x</span><span class="sxs-lookup"><span data-stu-id="17a85-109">.NET Core 1.x</span></span>](#tab/netcore1x)

```dotnetcli
dotnet [command] [arguments] [--additionalprobingpath] [--depsfile] [-d|--diagnostics]
    [--fx-version] [-h|--help] [--info] [--runtimeconfig] [-v|--verbosity] [--version]
```

---

## <a name="description"></a><span data-ttu-id="17a85-110">Opis</span><span class="sxs-lookup"><span data-stu-id="17a85-110">Description</span></span>

<span data-ttu-id="17a85-111">`dotnet` jest narzędziem do zarządzania kodem źródłowym i plikami binarnymi programu .NET.</span><span class="sxs-lookup"><span data-stu-id="17a85-111">`dotnet` is a tool for managing .NET source code and binaries.</span></span> <span data-ttu-id="17a85-112">Udostępnia polecenia wykonujące określone zadania, takie jak [`dotnet build`](dotnet-build.md) i [`dotnet run`](dotnet-run.md).</span><span class="sxs-lookup"><span data-stu-id="17a85-112">It exposes commands that perform specific tasks, such as [`dotnet build`](dotnet-build.md) and [`dotnet run`](dotnet-run.md).</span></span> <span data-ttu-id="17a85-113">Każde polecenie definiuje własne argumenty.</span><span class="sxs-lookup"><span data-stu-id="17a85-113">Each command defines its own arguments.</span></span> <span data-ttu-id="17a85-114">Wpisz `--help` po każdym poleceniu, aby uzyskać dostęp do krótkiej dokumentacji pomocy.</span><span class="sxs-lookup"><span data-stu-id="17a85-114">Type `--help` after each command to access brief help documentation.</span></span>

<span data-ttu-id="17a85-115">`dotnet` można używać do uruchamiania aplikacji przez określenie biblioteki DLL aplikacji, takiej jak `dotnet myapp.dll`.</span><span class="sxs-lookup"><span data-stu-id="17a85-115">`dotnet` can be used to run applications, by specifying an application DLL, such as `dotnet myapp.dll`.</span></span> <span data-ttu-id="17a85-116">Zobacz [wdrażanie aplikacji .NET Core](../deploying/index.md) w celu uzyskania informacji na temat opcji wdrażania.</span><span class="sxs-lookup"><span data-stu-id="17a85-116">See [.NET Core application deployment](../deploying/index.md) for to learn about deployment options.</span></span>

## <a name="options"></a><span data-ttu-id="17a85-117">Opcje</span><span class="sxs-lookup"><span data-stu-id="17a85-117">Options</span></span>

# <a name="net-core-21"></a>[<span data-ttu-id="17a85-118">.NET Core 2,1</span><span class="sxs-lookup"><span data-stu-id="17a85-118">.NET Core 2.1</span></span>](#tab/netcore21)

`--additional-deps <PATH>`

<span data-ttu-id="17a85-119">Ścieżka do dodatkowego pliku *. deps. JSON* .</span><span class="sxs-lookup"><span data-stu-id="17a85-119">Path to an additional *.deps.json* file.</span></span>

`--additionalprobingpath <PATH>`

<span data-ttu-id="17a85-120">Ścieżka zawierająca zasady i zestawy do sondowania.</span><span class="sxs-lookup"><span data-stu-id="17a85-120">Path containing probing policy and assemblies to probe.</span></span>

`--depsfile`

<span data-ttu-id="17a85-121">Ścieżka do pliku *deps. JSON* .</span><span class="sxs-lookup"><span data-stu-id="17a85-121">Path to a *deps.json* file.</span></span>

<span data-ttu-id="17a85-122">Plik *deps. JSON* zawiera listę zależności, zależności kompilacji i informacje o wersji używane do rozwiązywania konfliktów zestawów.</span><span class="sxs-lookup"><span data-stu-id="17a85-122">A *deps.json* file contains a list of dependencies, compilation dependencies, and version information used to address assembly conflicts.</span></span> <span data-ttu-id="17a85-123">Aby uzyskać więcej informacji na temat tego pliku, zobacz [pliki konfiguracji środowiska uruchomieniowego](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md) w serwisie GitHub.</span><span class="sxs-lookup"><span data-stu-id="17a85-123">For more information about this file, see [Runtime Configuration Files](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md) on GitHub.</span></span>

`-d|--diagnostics`

<span data-ttu-id="17a85-124">Włącza diagnostykę danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="17a85-124">Enables diagnostic output.</span></span>

`--fx-version <VERSION>`

<span data-ttu-id="17a85-125">Wersja środowiska uruchomieniowego platformy .NET Core do użycia w celu uruchomienia aplikacji.</span><span class="sxs-lookup"><span data-stu-id="17a85-125">Version of the .NET Core runtime to use to run the application.</span></span>

`-h|--help`

<span data-ttu-id="17a85-126">Drukuje dokumentację dla danego polecenia, taką jak `dotnet build --help`.</span><span class="sxs-lookup"><span data-stu-id="17a85-126">Prints out documentation for a given command, such as `dotnet build --help`.</span></span> <span data-ttu-id="17a85-127">`dotnet --help` drukuje listę dostępnych poleceń.</span><span class="sxs-lookup"><span data-stu-id="17a85-127">`dotnet --help` prints a list of available commands.</span></span>

`--info`

<span data-ttu-id="17a85-128">Drukuje szczegółowe informacje na temat instalacji programu .NET Core i środowiska maszynowego, takiego jak bieżący system operacyjny, i zatwierdzania SHA dla wersji .NET Core.</span><span class="sxs-lookup"><span data-stu-id="17a85-128">Prints out detailed information about a .NET Core installation and the machine environment, such as the current operating system, and commit SHA of the .NET Core version.</span></span>

`--list-runtimes`

<span data-ttu-id="17a85-129">Wyświetla zainstalowane środowiska uruchomieniowe platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="17a85-129">Displays the installed .NET Core runtimes.</span></span>

`--list-sdks`

<span data-ttu-id="17a85-130">Wyświetla zainstalowane zestawy SDK platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="17a85-130">Displays the installed .NET Core SDKs.</span></span>

`--roll-forward-on-no-candidate-fx <N>`

<span data-ttu-id="17a85-131">Definiuje zachowanie, gdy wymagana architektura udostępniona jest niedostępna.</span><span class="sxs-lookup"><span data-stu-id="17a85-131">Defines behavior when the required shared framework is not available.</span></span> <span data-ttu-id="17a85-132">`N` mogą być następujące:</span><span class="sxs-lookup"><span data-stu-id="17a85-132">`N` can be:</span></span>

- <span data-ttu-id="17a85-133">`0` — Wyłącz nawet dodatkową wersję pomocniczą.</span><span class="sxs-lookup"><span data-stu-id="17a85-133">`0` - Disable even minor version roll forward.</span></span>
- <span data-ttu-id="17a85-134">`1` — przewinięcie do wersji pomocniczej, ale nie w wersji głównej.</span><span class="sxs-lookup"><span data-stu-id="17a85-134">`1` - Roll forward on minor version, but not on major version.</span></span> <span data-ttu-id="17a85-135">Jest to zachowanie domyślne.</span><span class="sxs-lookup"><span data-stu-id="17a85-135">This is the default behavior.</span></span>
- <span data-ttu-id="17a85-136">`2` — przewinięcie w przód do wersji pomocniczych i głównych.</span><span class="sxs-lookup"><span data-stu-id="17a85-136">`2` - Roll forward on minor and major versions.</span></span>

 <span data-ttu-id="17a85-137">Aby uzyskać więcej informacji, zobacz [przewinięcie do przodu](../whats-new/dotnet-core-2-1.md#roll-forward).</span><span class="sxs-lookup"><span data-stu-id="17a85-137">For more information, see [Roll forward](../whats-new/dotnet-core-2-1.md#roll-forward).</span></span>

`--runtimeconfig`

<span data-ttu-id="17a85-138">Ścieżka do pliku *runtimeconfig. JSON* .</span><span class="sxs-lookup"><span data-stu-id="17a85-138">Path to a *runtimeconfig.json* file.</span></span>

<span data-ttu-id="17a85-139">Plik *runtimeconfig. JSON* to plik konfiguracji zawierający ustawienia czasu wykonywania.</span><span class="sxs-lookup"><span data-stu-id="17a85-139">A *runtimeconfig.json* file is a configuration file containing run-time settings.</span></span> <span data-ttu-id="17a85-140">Aby uzyskać więcej informacji, zobacz [Ustawienia konfiguracji środowiska uruchomieniowego .NET Core](../run-time-config/index.md#runtimeconfigjson).</span><span class="sxs-lookup"><span data-stu-id="17a85-140">For more information, see [.NET Core run-time configuration settings](../run-time-config/index.md#runtimeconfigjson).</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="17a85-141">Ustawia poziom szczegółowości polecenia.</span><span class="sxs-lookup"><span data-stu-id="17a85-141">Sets the verbosity level of the command.</span></span> <span data-ttu-id="17a85-142">Dozwolone wartości to `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`i `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="17a85-142">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="17a85-143">Nieobsługiwane w każdym poleceniu; Aby określić, czy ta opcja jest dostępna, zobacz określoną stronę poleceń.</span><span class="sxs-lookup"><span data-stu-id="17a85-143">Not supported in every command; see specific command page to determine if this option is available.</span></span>

`--version`

<span data-ttu-id="17a85-144">Drukuje używaną wersję zestaw .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="17a85-144">Prints out the version of the .NET Core SDK in use.</span></span>

# <a name="net-core-20"></a>[<span data-ttu-id="17a85-145">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="17a85-145">.NET Core 2.0</span></span>](#tab/netcore20)

`--additional-deps <PATH>`

<span data-ttu-id="17a85-146">Ścieżka do dodatkowego pliku *. deps. JSON* .</span><span class="sxs-lookup"><span data-stu-id="17a85-146">Path to an additional *.deps.json* file.</span></span>

`--additionalprobingpath <PATH>`

<span data-ttu-id="17a85-147">Ścieżka zawierająca zasady i zestawy do sondowania.</span><span class="sxs-lookup"><span data-stu-id="17a85-147">Path containing probing policy and assemblies to probe.</span></span>

`--depsfile`

<span data-ttu-id="17a85-148">Ścieżka do pliku *deps. JSON* .</span><span class="sxs-lookup"><span data-stu-id="17a85-148">Path to a *deps.json* file.</span></span>

<span data-ttu-id="17a85-149">Plik *deps. JSON* zawiera listę zależności, zależności kompilacji i informacje o wersji używane do rozwiązywania konfliktów zestawów.</span><span class="sxs-lookup"><span data-stu-id="17a85-149">A *deps.json* file contains a list of dependencies, compilation dependencies and version information used to address assembly conflicts.</span></span> <span data-ttu-id="17a85-150">Aby uzyskać więcej informacji na temat tego pliku, zobacz [pliki konfiguracji środowiska uruchomieniowego w serwisie GitHub](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md).</span><span class="sxs-lookup"><span data-stu-id="17a85-150">For more details on this file, see [Runtime Configuration Files on GitHub](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md).</span></span>

`-d|--diagnostics`

<span data-ttu-id="17a85-151">Włącza diagnostykę danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="17a85-151">Enables diagnostic output.</span></span>

`--fx-version <VERSION>`

<span data-ttu-id="17a85-152">Wersja środowiska uruchomieniowego platformy .NET Core do użycia w celu uruchomienia aplikacji.</span><span class="sxs-lookup"><span data-stu-id="17a85-152">Version of the .NET Core runtime to use to run the application.</span></span>

`-h|--help`

<span data-ttu-id="17a85-153">Drukuje dokumentację dla danego polecenia, taką jak `dotnet build --help`.</span><span class="sxs-lookup"><span data-stu-id="17a85-153">Prints out documentation for a given command, such as `dotnet build --help`.</span></span> <span data-ttu-id="17a85-154">`dotnet --help` drukuje listę dostępnych poleceń.</span><span class="sxs-lookup"><span data-stu-id="17a85-154">`dotnet --help` prints a list of available commands.</span></span>

`--info`

<span data-ttu-id="17a85-155">Drukuje szczegółowe informacje na temat instalacji programu .NET Core i środowiska maszynowego, takiego jak bieżący system operacyjny, i zatwierdzania SHA dla wersji .NET Core.</span><span class="sxs-lookup"><span data-stu-id="17a85-155">Prints out detailed information about a .NET Core installation and the machine environment, such as the current operating system, and commit SHA of the .NET Core version.</span></span>

`--roll-forward-on-no-candidate-fx`

 <span data-ttu-id="17a85-156">Wyłącza opcję wycofywania wersji pomocniczej, jeśli jest ustawiona na `0`.</span><span class="sxs-lookup"><span data-stu-id="17a85-156">Disables minor version roll forward, if set to `0`.</span></span> <span data-ttu-id="17a85-157">Aby uzyskać więcej informacji, zobacz [przewinięcie do przodu](../whats-new/dotnet-core-2-1.md#roll-forward).</span><span class="sxs-lookup"><span data-stu-id="17a85-157">For more information, see [Roll forward](../whats-new/dotnet-core-2-1.md#roll-forward).</span></span>

`--runtimeconfig`

<span data-ttu-id="17a85-158">Ścieżka do pliku *runtimeconfig. JSON* .</span><span class="sxs-lookup"><span data-stu-id="17a85-158">Path to a *runtimeconfig.json* file.</span></span>

<span data-ttu-id="17a85-159">Plik *runtimeconfig. JSON* to plik konfiguracji zawierający ustawienia czasu wykonywania.</span><span class="sxs-lookup"><span data-stu-id="17a85-159">A *runtimeconfig.json* file is a configuration file containing run-time settings.</span></span> <span data-ttu-id="17a85-160">Aby uzyskać więcej informacji, zobacz [Ustawienia konfiguracji środowiska uruchomieniowego .NET Core](../run-time-config/index.md#runtimeconfigjson).</span><span class="sxs-lookup"><span data-stu-id="17a85-160">For more information, see [.NET Core run-time configuration settings](../run-time-config/index.md#runtimeconfigjson).</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="17a85-161">Ustawia poziom szczegółowości polecenia.</span><span class="sxs-lookup"><span data-stu-id="17a85-161">Sets the verbosity level of the command.</span></span> <span data-ttu-id="17a85-162">Dozwolone wartości to `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`i `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="17a85-162">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="17a85-163">Nieobsługiwane w każdym poleceniu; Aby określić, czy ta opcja jest dostępna, zobacz określoną stronę poleceń.</span><span class="sxs-lookup"><span data-stu-id="17a85-163">Not supported in every command; see specific command page to determine if this option is available.</span></span>

`--version`

<span data-ttu-id="17a85-164">Drukuje używaną wersję zestaw .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="17a85-164">Prints out the version of the .NET Core SDK in use.</span></span>

# <a name="net-core-1x"></a>[<span data-ttu-id="17a85-165">.NET Core 1. x</span><span class="sxs-lookup"><span data-stu-id="17a85-165">.NET Core 1.x</span></span>](#tab/netcore1x)

`--additionalprobingpath <PATH>`

<span data-ttu-id="17a85-166">Ścieżka zawierająca zasady i zestawy do sondowania.</span><span class="sxs-lookup"><span data-stu-id="17a85-166">Path containing probing policy and assemblies to probe.</span></span>

`--depsfile`

<span data-ttu-id="17a85-167">Ścieżka do pliku *deps. JSON* .</span><span class="sxs-lookup"><span data-stu-id="17a85-167">Path to a *deps.json* file.</span></span>

<span data-ttu-id="17a85-168">Plik *deps. JSON* zawiera listę zależności, zależności kompilacji i informacje o wersji używane do rozwiązywania konfliktów zestawów.</span><span class="sxs-lookup"><span data-stu-id="17a85-168">A *deps.json* file contains a list of dependencies, compilation dependencies and version information used to address assembly conflicts.</span></span> <span data-ttu-id="17a85-169">Aby uzyskać więcej informacji na temat tego pliku, zobacz [pliki konfiguracji środowiska uruchomieniowego w serwisie GitHub](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md).</span><span class="sxs-lookup"><span data-stu-id="17a85-169">For more details on this file, see [Runtime Configuration Files on GitHub](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md).</span></span>

`-d|--diagnostics`

<span data-ttu-id="17a85-170">Włącza diagnostykę danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="17a85-170">Enables diagnostic output.</span></span>

`--fx-version <VERSION>`

<span data-ttu-id="17a85-171">Wersja środowiska uruchomieniowego platformy .NET Core do użycia w celu uruchomienia aplikacji.</span><span class="sxs-lookup"><span data-stu-id="17a85-171">Version of the .NET Core runtime to use to run the application.</span></span>

`-h|--help`

<span data-ttu-id="17a85-172">Drukuje dokumentację dla danego polecenia, taką jak `dotnet build --help`.</span><span class="sxs-lookup"><span data-stu-id="17a85-172">Prints out documentation for a given command, such as `dotnet build --help`.</span></span> <span data-ttu-id="17a85-173">`dotnet --help` drukuje listę dostępnych poleceń.</span><span class="sxs-lookup"><span data-stu-id="17a85-173">`dotnet --help` prints a list of available commands.</span></span>

`--info`

<span data-ttu-id="17a85-174">Drukuje szczegółowe informacje na temat instalacji programu .NET Core i środowiska maszynowego, takiego jak bieżący system operacyjny, i zatwierdzania SHA dla wersji .NET Core.</span><span class="sxs-lookup"><span data-stu-id="17a85-174">Prints out detailed information about a .NET Core installation and the machine environment, such as the current operating system, and commit SHA of the .NET Core version.</span></span>

`--runtimeconfig`

<span data-ttu-id="17a85-175">Ścieżka do pliku *runtimeconfig. JSON* .</span><span class="sxs-lookup"><span data-stu-id="17a85-175">Path to a *runtimeconfig.json* file.</span></span>

<span data-ttu-id="17a85-176">Plik *runtimeconfig. JSON* to plik konfiguracji zawierający ustawienia czasu wykonywania.</span><span class="sxs-lookup"><span data-stu-id="17a85-176">A *runtimeconfig.json* file is a configuration file containing run-time settings.</span></span> <span data-ttu-id="17a85-177">Aby uzyskać więcej informacji, zobacz [Ustawienia konfiguracji środowiska uruchomieniowego .NET Core](../run-time-config/index.md#runtimeconfigjson).</span><span class="sxs-lookup"><span data-stu-id="17a85-177">For more information, see [.NET Core run-time configuration settings](../run-time-config/index.md#runtimeconfigjson).</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="17a85-178">Ustawia poziom szczegółowości polecenia.</span><span class="sxs-lookup"><span data-stu-id="17a85-178">Sets the verbosity level of the command.</span></span> <span data-ttu-id="17a85-179">Dozwolone wartości to `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`i `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="17a85-179">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="17a85-180">Nieobsługiwane w każdym poleceniu; Aby określić, czy ta opcja jest dostępna, zobacz określoną stronę poleceń.</span><span class="sxs-lookup"><span data-stu-id="17a85-180">Not supported in every command; see specific command page to determine if this option is available.</span></span>

`--version`

<span data-ttu-id="17a85-181">Drukuje używaną wersję zestaw .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="17a85-181">Prints out the version of the .NET Core SDK in use.</span></span>

---

## <a name="dotnet-commands"></a><span data-ttu-id="17a85-182">Polecenia dotnet</span><span class="sxs-lookup"><span data-stu-id="17a85-182">dotnet commands</span></span>

### <a name="general"></a><span data-ttu-id="17a85-183">Ogólne</span><span class="sxs-lookup"><span data-stu-id="17a85-183">General</span></span>

# <a name="net-core-21"></a>[<span data-ttu-id="17a85-184">.NET Core 2,1</span><span class="sxs-lookup"><span data-stu-id="17a85-184">.NET Core 2.1</span></span>](#tab/netcore21)

| <span data-ttu-id="17a85-185">Polecenie</span><span class="sxs-lookup"><span data-stu-id="17a85-185">Command</span></span>                                       | <span data-ttu-id="17a85-186">Funkcja</span><span class="sxs-lookup"><span data-stu-id="17a85-186">Function</span></span>                                                            |
| --------------------------------------------- | ------------------------------------------------------------------- |
| [<span data-ttu-id="17a85-187">dotnet build</span><span class="sxs-lookup"><span data-stu-id="17a85-187">dotnet build</span></span>](dotnet-build.md)               | <span data-ttu-id="17a85-188">Kompiluje aplikację platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="17a85-188">Builds a .NET Core application.</span></span>                                     |
| [<span data-ttu-id="17a85-189">dotnet build-server</span><span class="sxs-lookup"><span data-stu-id="17a85-189">dotnet build-server</span></span>](dotnet-build-server.md) | <span data-ttu-id="17a85-190">Współdziała z serwerami uruchomionymi przez kompilację.</span><span class="sxs-lookup"><span data-stu-id="17a85-190">Interacts with servers started by a build.</span></span>                          |
| [<span data-ttu-id="17a85-191">dotnet clean</span><span class="sxs-lookup"><span data-stu-id="17a85-191">dotnet clean</span></span>](dotnet-clean.md)               | <span data-ttu-id="17a85-192">Czyste dane wyjściowe kompilacji.</span><span class="sxs-lookup"><span data-stu-id="17a85-192">Clean build outputs.</span></span>                                                |
| [<span data-ttu-id="17a85-193">dotnet help</span><span class="sxs-lookup"><span data-stu-id="17a85-193">dotnet help</span></span>](dotnet-help.md)                 | <span data-ttu-id="17a85-194">Przedstawia bardziej szczegółową dokumentację dla polecenia w trybie online.</span><span class="sxs-lookup"><span data-stu-id="17a85-194">Shows more detailed documentation online for the command.</span></span>           |
| [<span data-ttu-id="17a85-195">dotnet migrate</span><span class="sxs-lookup"><span data-stu-id="17a85-195">dotnet migrate</span></span>](dotnet-migrate.md)           | <span data-ttu-id="17a85-196">Migruje prawidłowy projekt w wersji zapoznawczej 2 do projektu zestaw .NET Core SDK 1,0.</span><span class="sxs-lookup"><span data-stu-id="17a85-196">Migrates a valid Preview 2 project to a .NET Core SDK 1.0 project.</span></span>  |
| [<span data-ttu-id="17a85-197">dotnet msbuild</span><span class="sxs-lookup"><span data-stu-id="17a85-197">dotnet msbuild</span></span>](dotnet-msbuild.md)           | <span data-ttu-id="17a85-198">Zapewnia dostęp do wiersza polecenia programu MSBuild.</span><span class="sxs-lookup"><span data-stu-id="17a85-198">Provides access to the MSBuild command line.</span></span>                        |
| [<span data-ttu-id="17a85-199">dotnet new</span><span class="sxs-lookup"><span data-stu-id="17a85-199">dotnet new</span></span>](dotnet-new.md)                   | <span data-ttu-id="17a85-200">Inicjuje projekt C# lub F# dla danego szablonu.</span><span class="sxs-lookup"><span data-stu-id="17a85-200">Initializes a C# or F# project for a given template.</span></span>                |
| [<span data-ttu-id="17a85-201">dotnet pack</span><span class="sxs-lookup"><span data-stu-id="17a85-201">dotnet pack</span></span>](dotnet-pack.md)                 | <span data-ttu-id="17a85-202">Tworzy pakiet NuGet kodu.</span><span class="sxs-lookup"><span data-stu-id="17a85-202">Creates a NuGet package of your code.</span></span>                               |
| [<span data-ttu-id="17a85-203">dotnet publish</span><span class="sxs-lookup"><span data-stu-id="17a85-203">dotnet publish</span></span>](dotnet-publish.md)           | <span data-ttu-id="17a85-204">Publikuje zależne od programu .NET Framework lub samodzielną aplikację.</span><span class="sxs-lookup"><span data-stu-id="17a85-204">Publishes a .NET framework-dependent or self-contained application.</span></span> |
| [<span data-ttu-id="17a85-205">dotnet restore</span><span class="sxs-lookup"><span data-stu-id="17a85-205">dotnet restore</span></span>](dotnet-restore.md)           | <span data-ttu-id="17a85-206">Przywraca zależności dla danej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="17a85-206">Restores the dependencies for a given application.</span></span>                  |
| [<span data-ttu-id="17a85-207">dotnet run</span><span class="sxs-lookup"><span data-stu-id="17a85-207">dotnet run</span></span>](dotnet-run.md)                   | <span data-ttu-id="17a85-208">Uruchamia aplikację ze źródła.</span><span class="sxs-lookup"><span data-stu-id="17a85-208">Runs the application from source.</span></span>                                   |
| [<span data-ttu-id="17a85-209">dotnet sln</span><span class="sxs-lookup"><span data-stu-id="17a85-209">dotnet sln</span></span>](dotnet-sln.md)                   | <span data-ttu-id="17a85-210">Opcje dodawania, usuwania i wyświetlania listy projektów w pliku rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="17a85-210">Options to add, remove, and list projects in a solution file.</span></span>       |
| [<span data-ttu-id="17a85-211">dotnet store</span><span class="sxs-lookup"><span data-stu-id="17a85-211">dotnet store</span></span>](dotnet-store.md)               | <span data-ttu-id="17a85-212">Przechowuje zestawy w magazynie pakietów środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="17a85-212">Stores assemblies in the runtime package store.</span></span>                     |
| [<span data-ttu-id="17a85-213">dotnet test</span><span class="sxs-lookup"><span data-stu-id="17a85-213">dotnet test</span></span>](dotnet-test.md)                 | <span data-ttu-id="17a85-214">Uruchamia testy przy użyciu modułu uruchamiającego testy.</span><span class="sxs-lookup"><span data-stu-id="17a85-214">Runs tests using a test runner.</span></span>                                     |

# <a name="net-core-20"></a>[<span data-ttu-id="17a85-215">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="17a85-215">.NET Core 2.0</span></span>](#tab/netcore20)

| <span data-ttu-id="17a85-216">Polecenie</span><span class="sxs-lookup"><span data-stu-id="17a85-216">Command</span></span>                             | <span data-ttu-id="17a85-217">Funkcja</span><span class="sxs-lookup"><span data-stu-id="17a85-217">Function</span></span>                                                            |
| ----------------------------------- | ------------------------------------------------------------------- |
| [<span data-ttu-id="17a85-218">dotnet build</span><span class="sxs-lookup"><span data-stu-id="17a85-218">dotnet build</span></span>](dotnet-build.md)     | <span data-ttu-id="17a85-219">Kompiluje aplikację platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="17a85-219">Builds a .NET Core application.</span></span>                                     |
| [<span data-ttu-id="17a85-220">dotnet clean</span><span class="sxs-lookup"><span data-stu-id="17a85-220">dotnet clean</span></span>](dotnet-clean.md)     | <span data-ttu-id="17a85-221">Czyste dane wyjściowe kompilacji.</span><span class="sxs-lookup"><span data-stu-id="17a85-221">Clean build outputs.</span></span>                                              |
| [<span data-ttu-id="17a85-222">dotnet help</span><span class="sxs-lookup"><span data-stu-id="17a85-222">dotnet help</span></span>](dotnet-help.md)       | <span data-ttu-id="17a85-223">Przedstawia bardziej szczegółową dokumentację dla polecenia w trybie online.</span><span class="sxs-lookup"><span data-stu-id="17a85-223">Shows more detailed documentation online for the command.</span></span>           |
| [<span data-ttu-id="17a85-224">dotnet migrate</span><span class="sxs-lookup"><span data-stu-id="17a85-224">dotnet migrate</span></span>](dotnet-migrate.md) | <span data-ttu-id="17a85-225">Migruje prawidłowy projekt w wersji zapoznawczej 2 do projektu zestaw .NET Core SDK 1,0.</span><span class="sxs-lookup"><span data-stu-id="17a85-225">Migrates a valid Preview 2 project to a .NET Core SDK 1.0 project.</span></span>  |
| [<span data-ttu-id="17a85-226">dotnet msbuild</span><span class="sxs-lookup"><span data-stu-id="17a85-226">dotnet msbuild</span></span>](dotnet-msbuild.md) | <span data-ttu-id="17a85-227">Zapewnia dostęp do wiersza polecenia programu MSBuild.</span><span class="sxs-lookup"><span data-stu-id="17a85-227">Provides access to the MSBuild command line.</span></span>                        |
| [<span data-ttu-id="17a85-228">dotnet new</span><span class="sxs-lookup"><span data-stu-id="17a85-228">dotnet new</span></span>](dotnet-new.md)         | <span data-ttu-id="17a85-229">Inicjuje projekt C# lub F# dla danego szablonu.</span><span class="sxs-lookup"><span data-stu-id="17a85-229">Initializes a C# or F# project for a given template.</span></span>                |
| [<span data-ttu-id="17a85-230">dotnet pack</span><span class="sxs-lookup"><span data-stu-id="17a85-230">dotnet pack</span></span>](dotnet-pack.md)       | <span data-ttu-id="17a85-231">Tworzy pakiet NuGet kodu.</span><span class="sxs-lookup"><span data-stu-id="17a85-231">Creates a NuGet package of your code.</span></span>                               |
| [<span data-ttu-id="17a85-232">dotnet publish</span><span class="sxs-lookup"><span data-stu-id="17a85-232">dotnet publish</span></span>](dotnet-publish.md) | <span data-ttu-id="17a85-233">Publikuje zależne od programu .NET Framework lub samodzielną aplikację.</span><span class="sxs-lookup"><span data-stu-id="17a85-233">Publishes a .NET framework-dependent or self-contained application.</span></span> |
| [<span data-ttu-id="17a85-234">dotnet restore</span><span class="sxs-lookup"><span data-stu-id="17a85-234">dotnet restore</span></span>](dotnet-restore.md) | <span data-ttu-id="17a85-235">Przywraca zależności dla danej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="17a85-235">Restores the dependencies for a given application.</span></span>                  |
| [<span data-ttu-id="17a85-236">dotnet run</span><span class="sxs-lookup"><span data-stu-id="17a85-236">dotnet run</span></span>](dotnet-run.md)         | <span data-ttu-id="17a85-237">Uruchamia aplikację ze źródła.</span><span class="sxs-lookup"><span data-stu-id="17a85-237">Runs the application from source.</span></span>                                   |
| [<span data-ttu-id="17a85-238">dotnet sln</span><span class="sxs-lookup"><span data-stu-id="17a85-238">dotnet sln</span></span>](dotnet-sln.md)         | <span data-ttu-id="17a85-239">Opcje dodawania, usuwania i wyświetlania listy projektów w pliku rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="17a85-239">Options to add, remove, and list projects in a solution file.</span></span>       |
| [<span data-ttu-id="17a85-240">dotnet store</span><span class="sxs-lookup"><span data-stu-id="17a85-240">dotnet store</span></span>](dotnet-store.md)     | <span data-ttu-id="17a85-241">Przechowuje zestawy w magazynie pakietów środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="17a85-241">Stores assemblies in the runtime package store.</span></span>                     |
| [<span data-ttu-id="17a85-242">dotnet test</span><span class="sxs-lookup"><span data-stu-id="17a85-242">dotnet test</span></span>](dotnet-test.md)       | <span data-ttu-id="17a85-243">Uruchamia testy przy użyciu modułu uruchamiającego testy.</span><span class="sxs-lookup"><span data-stu-id="17a85-243">Runs tests using a test runner.</span></span>                                     |

# <a name="net-core-1x"></a>[<span data-ttu-id="17a85-244">.NET Core 1. x</span><span class="sxs-lookup"><span data-stu-id="17a85-244">.NET Core 1.x</span></span>](#tab/netcore1x)

| <span data-ttu-id="17a85-245">Polecenie</span><span class="sxs-lookup"><span data-stu-id="17a85-245">Command</span></span>                             | <span data-ttu-id="17a85-246">Funkcja</span><span class="sxs-lookup"><span data-stu-id="17a85-246">Function</span></span>                                                            |
| ----------------------------------- | ------------------------------------------------------------------- |
| [<span data-ttu-id="17a85-247">dotnet build</span><span class="sxs-lookup"><span data-stu-id="17a85-247">dotnet build</span></span>](dotnet-build.md)     | <span data-ttu-id="17a85-248">Kompiluje aplikację platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="17a85-248">Builds a .NET Core application.</span></span>                                     |
| [<span data-ttu-id="17a85-249">dotnet clean</span><span class="sxs-lookup"><span data-stu-id="17a85-249">dotnet clean</span></span>](dotnet-clean.md)     | <span data-ttu-id="17a85-250">Czyste dane wyjściowe kompilacji.</span><span class="sxs-lookup"><span data-stu-id="17a85-250">Clean build outputs.</span></span>                                              |
| [<span data-ttu-id="17a85-251">dotnet migrate</span><span class="sxs-lookup"><span data-stu-id="17a85-251">dotnet migrate</span></span>](dotnet-migrate.md) | <span data-ttu-id="17a85-252">Migruje prawidłowy projekt w wersji zapoznawczej 2 do projektu zestaw .NET Core SDK 1,0.</span><span class="sxs-lookup"><span data-stu-id="17a85-252">Migrates a valid Preview 2 project to a .NET Core SDK 1.0 project.</span></span>  |
| [<span data-ttu-id="17a85-253">dotnet msbuild</span><span class="sxs-lookup"><span data-stu-id="17a85-253">dotnet msbuild</span></span>](dotnet-msbuild.md) | <span data-ttu-id="17a85-254">Zapewnia dostęp do wiersza polecenia programu MSBuild.</span><span class="sxs-lookup"><span data-stu-id="17a85-254">Provides access to the MSBuild command line.</span></span>                        |
| [<span data-ttu-id="17a85-255">dotnet new</span><span class="sxs-lookup"><span data-stu-id="17a85-255">dotnet new</span></span>](dotnet-new.md)         | <span data-ttu-id="17a85-256">Inicjuje projekt C# lub F# dla danego szablonu.</span><span class="sxs-lookup"><span data-stu-id="17a85-256">Initializes a C# or F# project for a given template.</span></span>                |
| [<span data-ttu-id="17a85-257">dotnet pack</span><span class="sxs-lookup"><span data-stu-id="17a85-257">dotnet pack</span></span>](dotnet-pack.md)       | <span data-ttu-id="17a85-258">Tworzy pakiet NuGet kodu.</span><span class="sxs-lookup"><span data-stu-id="17a85-258">Creates a NuGet package of your code.</span></span>                               |
| [<span data-ttu-id="17a85-259">dotnet publish</span><span class="sxs-lookup"><span data-stu-id="17a85-259">dotnet publish</span></span>](dotnet-publish.md) | <span data-ttu-id="17a85-260">Publikuje zależne od programu .NET Framework lub samodzielną aplikację.</span><span class="sxs-lookup"><span data-stu-id="17a85-260">Publishes a .NET framework-dependent or self-contained application.</span></span> |
| [<span data-ttu-id="17a85-261">dotnet restore</span><span class="sxs-lookup"><span data-stu-id="17a85-261">dotnet restore</span></span>](dotnet-restore.md) | <span data-ttu-id="17a85-262">Przywraca zależności dla danej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="17a85-262">Restores the dependencies for a given application.</span></span>                  |
| [<span data-ttu-id="17a85-263">dotnet run</span><span class="sxs-lookup"><span data-stu-id="17a85-263">dotnet run</span></span>](dotnet-run.md)         | <span data-ttu-id="17a85-264">Uruchamia aplikację ze źródła.</span><span class="sxs-lookup"><span data-stu-id="17a85-264">Runs the application from source.</span></span>                                   |
| [<span data-ttu-id="17a85-265">dotnet sln</span><span class="sxs-lookup"><span data-stu-id="17a85-265">dotnet sln</span></span>](dotnet-sln.md)         | <span data-ttu-id="17a85-266">Opcje dodawania, usuwania i wyświetlania listy projektów w pliku rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="17a85-266">Options to add, remove, and list projects in a solution file.</span></span>       |
| [<span data-ttu-id="17a85-267">dotnet test</span><span class="sxs-lookup"><span data-stu-id="17a85-267">dotnet test</span></span>](dotnet-test.md)       | <span data-ttu-id="17a85-268">Uruchamia testy przy użyciu modułu uruchamiającego testy.</span><span class="sxs-lookup"><span data-stu-id="17a85-268">Runs tests using a test runner.</span></span>                                     |

---

### <a name="project-references"></a><span data-ttu-id="17a85-269">Odwołania projektu</span><span class="sxs-lookup"><span data-stu-id="17a85-269">Project references</span></span>

<span data-ttu-id="17a85-270">Polecenie</span><span class="sxs-lookup"><span data-stu-id="17a85-270">Command</span></span> | <span data-ttu-id="17a85-271">Funkcja</span><span class="sxs-lookup"><span data-stu-id="17a85-271">Function</span></span>
--- | ---
[<span data-ttu-id="17a85-272">dotnet add reference</span><span class="sxs-lookup"><span data-stu-id="17a85-272">dotnet add reference</span></span>](dotnet-add-reference.md) | <span data-ttu-id="17a85-273">Dodaje odwołanie do projektu.</span><span class="sxs-lookup"><span data-stu-id="17a85-273">Adds a project reference.</span></span>
[<span data-ttu-id="17a85-274">dotnet list reference</span><span class="sxs-lookup"><span data-stu-id="17a85-274">dotnet list reference</span></span>](dotnet-list-reference.md) | <span data-ttu-id="17a85-275">Wyświetla listę odwołań do projektu.</span><span class="sxs-lookup"><span data-stu-id="17a85-275">Lists project references.</span></span>
[<span data-ttu-id="17a85-276">dotnet remove reference</span><span class="sxs-lookup"><span data-stu-id="17a85-276">dotnet remove reference</span></span>](dotnet-remove-reference.md) | <span data-ttu-id="17a85-277">Usuwa odwołanie do projektu.</span><span class="sxs-lookup"><span data-stu-id="17a85-277">Removes a project reference.</span></span>

### <a name="nuget-packages"></a><span data-ttu-id="17a85-278">Pakiety NuGet</span><span class="sxs-lookup"><span data-stu-id="17a85-278">NuGet packages</span></span>

<span data-ttu-id="17a85-279">Polecenie</span><span class="sxs-lookup"><span data-stu-id="17a85-279">Command</span></span> | <span data-ttu-id="17a85-280">Funkcja</span><span class="sxs-lookup"><span data-stu-id="17a85-280">Function</span></span>
--- | ---
[<span data-ttu-id="17a85-281">dotnet add package</span><span class="sxs-lookup"><span data-stu-id="17a85-281">dotnet add package</span></span>](dotnet-add-package.md) | <span data-ttu-id="17a85-282">Dodaje pakiet NuGet.</span><span class="sxs-lookup"><span data-stu-id="17a85-282">Adds a NuGet package.</span></span>
[<span data-ttu-id="17a85-283">dotnet remove package</span><span class="sxs-lookup"><span data-stu-id="17a85-283">dotnet remove package</span></span>](dotnet-remove-package.md) | <span data-ttu-id="17a85-284">Usuwa pakiet NuGet.</span><span class="sxs-lookup"><span data-stu-id="17a85-284">Removes a NuGet package.</span></span>

### <a name="nuget-commands"></a><span data-ttu-id="17a85-285">Polecenia NuGet</span><span class="sxs-lookup"><span data-stu-id="17a85-285">NuGet commands</span></span>

<span data-ttu-id="17a85-286">Polecenie</span><span class="sxs-lookup"><span data-stu-id="17a85-286">Command</span></span> | <span data-ttu-id="17a85-287">Funkcja</span><span class="sxs-lookup"><span data-stu-id="17a85-287">Function</span></span>
--- | ---
[<span data-ttu-id="17a85-288">dotnet nuget delete</span><span class="sxs-lookup"><span data-stu-id="17a85-288">dotnet nuget delete</span></span>](dotnet-nuget-delete.md) | <span data-ttu-id="17a85-289">Usuwa pakiet z serwera lub go wystawia.</span><span class="sxs-lookup"><span data-stu-id="17a85-289">Deletes or unlists a package from the server.</span></span>
[<span data-ttu-id="17a85-290">dotnet nuget locals</span><span class="sxs-lookup"><span data-stu-id="17a85-290">dotnet nuget locals</span></span>](dotnet-nuget-locals.md) | <span data-ttu-id="17a85-291">Czyści lub wyświetla lokalne zasoby NuGet, takie jak pamięć podręczna żądań HTTP, tymczasowa pamięć podręczna lub folder pakietów globalnych dla całego komputera.</span><span class="sxs-lookup"><span data-stu-id="17a85-291">Clears or lists local NuGet resources such as http-request cache, temporary cache, or machine-wide global packages folder.</span></span>
[<span data-ttu-id="17a85-292">dotnet nuget push</span><span class="sxs-lookup"><span data-stu-id="17a85-292">dotnet nuget push</span></span>](dotnet-nuget-push.md) | <span data-ttu-id="17a85-293">Wypchnij pakiet na serwer i opublikuje go.</span><span class="sxs-lookup"><span data-stu-id="17a85-293">Pushes a package to the server and publishes it.</span></span>

### <a name="global-tool-path-and-local-tools-commands"></a><span data-ttu-id="17a85-294">Globalne, ścieżki narzędziowe i polecenia narzędzi lokalnych</span><span class="sxs-lookup"><span data-stu-id="17a85-294">Global, tool-path, and local tools commands</span></span>

<span data-ttu-id="17a85-295">Narzędzia są aplikacjami konsolowymi, które są instalowane z pakietów NuGet i są wywoływane z wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="17a85-295">Tools are console applications that are installed from NuGet packages and are invoked from the command prompt.</span></span> <span data-ttu-id="17a85-296">Narzędzia można pisać samodzielnie lub instalować Narzędzia zapisane przez inne firmy.</span><span class="sxs-lookup"><span data-stu-id="17a85-296">You can write tools yourself or install tools written by third parties.</span></span> <span data-ttu-id="17a85-297">Narzędzia są również nazywane narzędziami globalnymi, narzędziami ścieżki narzędzi i narzędziami lokalnymi.</span><span class="sxs-lookup"><span data-stu-id="17a85-297">Tools are also known as global tools, tool-path tools, and local tools.</span></span> <span data-ttu-id="17a85-298">Aby uzyskać więcej informacji, zobacz [Narzędzia platformy .NET Core — Omówienie](global-tools.md).</span><span class="sxs-lookup"><span data-stu-id="17a85-298">For more information, see [.NET Core tools overview](global-tools.md).</span></span> <span data-ttu-id="17a85-299">Narzędzia globalne i ścieżki narzędzi są dostępne począwszy od zestaw .NET Core SDK 2,1.</span><span class="sxs-lookup"><span data-stu-id="17a85-299">Global and tool-path tools are available starting with .NET Core SDK 2.1.</span></span> <span data-ttu-id="17a85-300">Narzędzia lokalne są dostępne począwszy od zestaw .NET Core SDK 3,0.</span><span class="sxs-lookup"><span data-stu-id="17a85-300">Local tools are available starting with .NET Core SDK 3.0.</span></span>

<span data-ttu-id="17a85-301">Polecenie</span><span class="sxs-lookup"><span data-stu-id="17a85-301">Command</span></span> | <span data-ttu-id="17a85-302">Funkcja</span><span class="sxs-lookup"><span data-stu-id="17a85-302">Function</span></span>
--- | ---
[<span data-ttu-id="17a85-303">dotnet tool install</span><span class="sxs-lookup"><span data-stu-id="17a85-303">dotnet tool install</span></span>](dotnet-tool-install.md) | <span data-ttu-id="17a85-304">Instaluje narzędzie na komputerze.</span><span class="sxs-lookup"><span data-stu-id="17a85-304">Installs a tool on your machine.</span></span>
[<span data-ttu-id="17a85-305">dotnet tool list</span><span class="sxs-lookup"><span data-stu-id="17a85-305">dotnet tool list</span></span>](dotnet-tool-list.md) | <span data-ttu-id="17a85-306">Wyświetla listę wszystkich globalnych narzędzi, ścieżek narzędziowych lub lokalnych zainstalowanych obecnie na komputerze.</span><span class="sxs-lookup"><span data-stu-id="17a85-306">Lists all global, tool-path, or local tools currently installed on your machine.</span></span>
[<span data-ttu-id="17a85-307">dotnet tool uninstall</span><span class="sxs-lookup"><span data-stu-id="17a85-307">dotnet tool uninstall</span></span>](dotnet-tool-uninstall.md) | <span data-ttu-id="17a85-308">Odinstalowuje narzędzie z komputera.</span><span class="sxs-lookup"><span data-stu-id="17a85-308">Uninstalls a tool from your machine.</span></span>
[<span data-ttu-id="17a85-309">dotnet tool update</span><span class="sxs-lookup"><span data-stu-id="17a85-309">dotnet tool update</span></span>](dotnet-tool-update.md) | <span data-ttu-id="17a85-310">Aktualizuje narzędzie zainstalowane na komputerze.</span><span class="sxs-lookup"><span data-stu-id="17a85-310">Updates a tool that is installed on your machine.</span></span>

### <a name="additional-tools"></a><span data-ttu-id="17a85-311">Dodatkowe narzędzia</span><span class="sxs-lookup"><span data-stu-id="17a85-311">Additional tools</span></span>

<span data-ttu-id="17a85-312">Począwszy od zestaw .NET Core SDK 2.1.300, wiele narzędzi, które były dostępne tylko dla poszczególnych projektów, przy użyciu `DotnetCliToolReference`, są teraz dostępne jako część zestaw .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="17a85-312">Starting with .NET Core SDK 2.1.300, a number of tools that were available only on a per project basis using `DotnetCliToolReference` are now available as part of the .NET Core SDK.</span></span> <span data-ttu-id="17a85-313">Te narzędzia są wymienione w poniższej tabeli:</span><span class="sxs-lookup"><span data-stu-id="17a85-313">These tools are listed in the following table:</span></span>

| <span data-ttu-id="17a85-314">Narzędzie</span><span class="sxs-lookup"><span data-stu-id="17a85-314">Tool</span></span>                                              | <span data-ttu-id="17a85-315">Funkcja</span><span class="sxs-lookup"><span data-stu-id="17a85-315">Function</span></span>                                                     |
| ------------------------------------------------- | ------------------------------------------------------------ |
| <span data-ttu-id="17a85-316">dev-certs</span><span class="sxs-lookup"><span data-stu-id="17a85-316">dev-certs</span></span>                                         | <span data-ttu-id="17a85-317">Tworzy i zarządza certyfikatami deweloperskimi.</span><span class="sxs-lookup"><span data-stu-id="17a85-317">Creates and manages development certificates.</span></span>                |
| [<span data-ttu-id="17a85-318">bieżąco</span><span class="sxs-lookup"><span data-stu-id="17a85-318">ef</span></span>](/ef/core/miscellaneous/cli/dotnet)           | <span data-ttu-id="17a85-319">Entity Framework Core narzędzia wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="17a85-319">Entity Framework Core command-line tools.</span></span>                    |
| <span data-ttu-id="17a85-320">SQL-pamięć podręczna</span><span class="sxs-lookup"><span data-stu-id="17a85-320">sql-cache</span></span>                                         | <span data-ttu-id="17a85-321">SQL Server narzędzia wiersza polecenia pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="17a85-321">SQL Server cache command-line tools.</span></span>                         |
| [<span data-ttu-id="17a85-322">wpisy tajne użytkownika</span><span class="sxs-lookup"><span data-stu-id="17a85-322">user-secrets</span></span>](/aspnet/core/security/app-secrets) | <span data-ttu-id="17a85-323">Zarządza kluczami tajnymi użytkowników deweloperskich.</span><span class="sxs-lookup"><span data-stu-id="17a85-323">Manages development user secrets.</span></span>                            |
| [<span data-ttu-id="17a85-324">Obejrzyj</span><span class="sxs-lookup"><span data-stu-id="17a85-324">watch</span></span>](/aspnet/core/tutorials/dotnet-watch)      | <span data-ttu-id="17a85-325">Uruchamia obserwatora plików, który uruchamia polecenie, gdy pliki zmienią się.</span><span class="sxs-lookup"><span data-stu-id="17a85-325">Starts a file watcher that runs a command when files change.</span></span> |

<span data-ttu-id="17a85-326">Aby uzyskać więcej informacji na temat każdego narzędzia, wpisz `dotnet <tool-name> --help`.</span><span class="sxs-lookup"><span data-stu-id="17a85-326">For more information about each tool, type `dotnet <tool-name> --help`.</span></span>

## <a name="examples"></a><span data-ttu-id="17a85-327">Przykłady</span><span class="sxs-lookup"><span data-stu-id="17a85-327">Examples</span></span>

<span data-ttu-id="17a85-328">Tworzy nową aplikację konsolową platformy .NET Core:</span><span class="sxs-lookup"><span data-stu-id="17a85-328">Creates a new .NET Core console application:</span></span>

`dotnet new console`

<span data-ttu-id="17a85-329">Przywróć zależności dla danej aplikacji:</span><span class="sxs-lookup"><span data-stu-id="17a85-329">Restore dependencies for a given application:</span></span>

`dotnet restore`

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

<span data-ttu-id="17a85-330">Kompiluj projekt i jego zależności w danym katalogu:</span><span class="sxs-lookup"><span data-stu-id="17a85-330">Build a project and its dependencies in a given directory:</span></span>

`dotnet build`

<span data-ttu-id="17a85-331">Uruchom bibliotekę DLL aplikacji, taką jak `myapp.dll`:</span><span class="sxs-lookup"><span data-stu-id="17a85-331">Run an application DLL, such as `myapp.dll`:</span></span>

`dotnet myapp.dll`

## <a name="environment-variables"></a><span data-ttu-id="17a85-332">Zmienne środowiskowe</span><span class="sxs-lookup"><span data-stu-id="17a85-332">Environment variables</span></span>

# <a name="net-core-21"></a>[<span data-ttu-id="17a85-333">.NET Core 2,1</span><span class="sxs-lookup"><span data-stu-id="17a85-333">.NET Core 2.1</span></span>](#tab/netcore21)

`DOTNET_PACKAGES`

<span data-ttu-id="17a85-334">Folder pakiety globalne.</span><span class="sxs-lookup"><span data-stu-id="17a85-334">The global packages folder.</span></span> <span data-ttu-id="17a85-335">Jeśli nie zostanie ustawiona, domyślnie jest `~/.nuget/packages` w systemie UNIX lub `%userprofile%\.nuget\packages` na komputerze z systemem Windows.</span><span class="sxs-lookup"><span data-stu-id="17a85-335">If not set, it defaults to `~/.nuget/packages` on Unix or `%userprofile%\.nuget\packages` on Windows.</span></span>

`DOTNET_SERVICING`

<span data-ttu-id="17a85-336">Określa lokalizację indeksu obsługi, który ma być używany przez host udostępniony podczas ładowania środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="17a85-336">Specifies the location of the servicing index to use by the shared host when loading the runtime.</span></span>

`DOTNET_CLI_TELEMETRY_OPTOUT`

<span data-ttu-id="17a85-337">Określa, czy dane dotyczące użycia narzędzi .NET Core są zbierane i wysyłane do firmy Microsoft.</span><span class="sxs-lookup"><span data-stu-id="17a85-337">Specifies whether data about the .NET Core tools usage is collected and sent to Microsoft.</span></span> <span data-ttu-id="17a85-338">Ustaw `true`, aby zrezygnować z funkcji telemetrii (wartości `true`, `1`lub `yes` zaakceptowane).</span><span class="sxs-lookup"><span data-stu-id="17a85-338">Set to `true` to opt-out of the telemetry feature (values `true`, `1`, or `yes` accepted).</span></span> <span data-ttu-id="17a85-339">W przeciwnym razie ustaw wartość `false`, aby zrezygnować z funkcji telemetrii (wartości `false`, `0`lub `no` zaakceptowane).</span><span class="sxs-lookup"><span data-stu-id="17a85-339">Otherwise, set to `false` to opt into the telemetry features (values `false`, `0`, or `no` accepted).</span></span> <span data-ttu-id="17a85-340">Jeśli nie zostanie ustawiona, wartość domyślna to `false` i aktywna jest funkcja telemetrii.</span><span class="sxs-lookup"><span data-stu-id="17a85-340">If not set, the default is `false` and the telemetry feature is active.</span></span>

`DOTNET_MULTILEVEL_LOOKUP`

<span data-ttu-id="17a85-341">Określa, czy środowisko uruchomieniowe programu .NET Core, udostępnione środowisko lub zestaw SDK są rozpoznawane z lokalizacji globalnej.</span><span class="sxs-lookup"><span data-stu-id="17a85-341">Specifies whether .NET Core runtime, shared framework, or SDK are resolved from the global location.</span></span> <span data-ttu-id="17a85-342">Jeśli nie zostanie ustawiona, domyślnie `true`.</span><span class="sxs-lookup"><span data-stu-id="17a85-342">If not set, it defaults to `true`.</span></span> <span data-ttu-id="17a85-343">Ustaw `false`, aby nie rozwiązany z lokalizacji globalnej i mieć izolowane instalacje platformy .NET Core (wartości `0` lub `false` są akceptowane).</span><span class="sxs-lookup"><span data-stu-id="17a85-343">Set to `false` to not resolve from the global location and have isolated .NET Core installations (values `0` or `false` are accepted).</span></span> <span data-ttu-id="17a85-344">Aby uzyskać więcej informacji o wyszukiwaniu wielu poziomów, zobacz [SharedFX wyszukiwanie na wielu poziomach](https://github.com/dotnet/core-setup/blob/master/Documentation/design-docs/multilevel-sharedfx-lookup.md).</span><span class="sxs-lookup"><span data-stu-id="17a85-344">For more information about multi-level lookup, see [Multi-level SharedFX Lookup](https://github.com/dotnet/core-setup/blob/master/Documentation/design-docs/multilevel-sharedfx-lookup.md).</span></span>

`DOTNET_ROLL_FORWARD_ON_NO_CANDIDATE_FX`

<span data-ttu-id="17a85-345">Wyłącza opcję wycofywania wersji pomocniczej, jeśli jest ustawiona na `0`.</span><span class="sxs-lookup"><span data-stu-id="17a85-345">Disables minor version roll forward, if set to `0`.</span></span> <span data-ttu-id="17a85-346">Aby uzyskać więcej informacji, zobacz [przewinięcie do przodu](../whats-new/dotnet-core-2-1.md#roll-forward).</span><span class="sxs-lookup"><span data-stu-id="17a85-346">For more information, see [Roll forward](../whats-new/dotnet-core-2-1.md#roll-forward).</span></span>

# <a name="net-core-20"></a>[<span data-ttu-id="17a85-347">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="17a85-347">.NET Core 2.0</span></span>](#tab/netcore20)

`DOTNET_PACKAGES`

<span data-ttu-id="17a85-348">Podstawowa pamięć podręczna pakietu.</span><span class="sxs-lookup"><span data-stu-id="17a85-348">The primary package cache.</span></span> <span data-ttu-id="17a85-349">Jeśli nie zostanie ustawiona, domyślnie jest `$HOME/.nuget/packages` w systemie UNIX lub `%userprofile%\.nuget\packages` na komputerze z systemem Windows.</span><span class="sxs-lookup"><span data-stu-id="17a85-349">If not set, it defaults to `$HOME/.nuget/packages` on Unix or `%userprofile%\.nuget\packages` on Windows.</span></span>

`DOTNET_SERVICING`

<span data-ttu-id="17a85-350">Określa lokalizację indeksu obsługi, który ma być używany przez host udostępniony podczas ładowania środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="17a85-350">Specifies the location of the servicing index to use by the shared host when loading the runtime.</span></span>

`DOTNET_CLI_TELEMETRY_OPTOUT`

<span data-ttu-id="17a85-351">Określa, czy dane dotyczące użycia narzędzi .NET Core są zbierane i wysyłane do firmy Microsoft.</span><span class="sxs-lookup"><span data-stu-id="17a85-351">Specifies whether data about the .NET Core tools usage is collected and sent to Microsoft.</span></span> <span data-ttu-id="17a85-352">Ustaw `true`, aby zrezygnować z funkcji telemetrii (wartości `true`, `1`lub `yes` zaakceptowane).</span><span class="sxs-lookup"><span data-stu-id="17a85-352">Set to `true` to opt-out of the telemetry feature (values `true`, `1`, or `yes` accepted).</span></span> <span data-ttu-id="17a85-353">W przeciwnym razie ustaw wartość `false`, aby zrezygnować z funkcji telemetrii (wartości `false`, `0`lub `no` zaakceptowane).</span><span class="sxs-lookup"><span data-stu-id="17a85-353">Otherwise, set to `false` to opt into the telemetry features (values `false`, `0`, or `no` accepted).</span></span> <span data-ttu-id="17a85-354">Jeśli nie zostanie ustawiona, wartość domyślna to `false` i aktywna jest funkcja telemetrii.</span><span class="sxs-lookup"><span data-stu-id="17a85-354">If not set, the default is `false` and the telemetry feature is active.</span></span>

`DOTNET_MULTILEVEL_LOOKUP`

<span data-ttu-id="17a85-355">Określa, czy środowisko uruchomieniowe programu .NET Core, udostępnione środowisko lub zestaw SDK są rozpoznawane z lokalizacji globalnej.</span><span class="sxs-lookup"><span data-stu-id="17a85-355">Specifies whether .NET Core runtime, shared framework, or SDK are resolved from the global location.</span></span> <span data-ttu-id="17a85-356">Jeśli nie zostanie ustawiona, domyślnie `true`.</span><span class="sxs-lookup"><span data-stu-id="17a85-356">If not set, it defaults to `true`.</span></span> <span data-ttu-id="17a85-357">Ustaw `false`, aby nie rozwiązany z lokalizacji globalnej i mieć izolowane instalacje platformy .NET Core (wartości `0` lub `false` są akceptowane).</span><span class="sxs-lookup"><span data-stu-id="17a85-357">Set to `false` to not resolve from the global location and have isolated .NET Core installations (values `0` or `false` are accepted).</span></span> <span data-ttu-id="17a85-358">Aby uzyskać więcej informacji o wyszukiwaniu wielu poziomów, zobacz [SharedFX wyszukiwanie na wielu poziomach](https://github.com/dotnet/core-setup/blob/master/Documentation/design-docs/multilevel-sharedfx-lookup.md).</span><span class="sxs-lookup"><span data-stu-id="17a85-358">For more information about multi-level lookup, see [Multi-level SharedFX Lookup](https://github.com/dotnet/core-setup/blob/master/Documentation/design-docs/multilevel-sharedfx-lookup.md).</span></span>

# <a name="net-core-1x"></a>[<span data-ttu-id="17a85-359">.NET Core 1. x</span><span class="sxs-lookup"><span data-stu-id="17a85-359">.NET Core 1.x</span></span>](#tab/netcore1x)

`DOTNET_PACKAGES`

<span data-ttu-id="17a85-360">Podstawowa pamięć podręczna pakietu.</span><span class="sxs-lookup"><span data-stu-id="17a85-360">The primary package cache.</span></span> <span data-ttu-id="17a85-361">Jeśli nie zostanie ustawiona, domyślnie jest `$HOME/.nuget/packages` w systemie UNIX lub `%userprofile%\.nuget\packages` na komputerze z systemem Windows.</span><span class="sxs-lookup"><span data-stu-id="17a85-361">If not set, it defaults to `$HOME/.nuget/packages` on Unix or `%userprofile%\.nuget\packages` on Windows.</span></span>

`DOTNET_SERVICING`

<span data-ttu-id="17a85-362">Określa lokalizację indeksu obsługi, który ma być używany przez host udostępniony podczas ładowania środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="17a85-362">Specifies the location of the servicing index to use by the shared host when loading the runtime.</span></span>

`DOTNET_CLI_TELEMETRY_OPTOUT`

<span data-ttu-id="17a85-363">Określa, czy dane dotyczące użycia narzędzi .NET Core są zbierane i wysyłane do firmy Microsoft.</span><span class="sxs-lookup"><span data-stu-id="17a85-363">Specifies whether data about the .NET Core tools usage is collected and sent to Microsoft.</span></span> <span data-ttu-id="17a85-364">Ustaw `true`, aby zrezygnować z funkcji telemetrii (wartości `true`, `1`lub `yes` zaakceptowane).</span><span class="sxs-lookup"><span data-stu-id="17a85-364">Set to `true` to opt-out of the telemetry feature (values `true`, `1`, or `yes` accepted).</span></span> <span data-ttu-id="17a85-365">W przeciwnym razie ustaw wartość `false`, aby zrezygnować z funkcji telemetrii (wartości `false`, `0`lub `no` zaakceptowane).</span><span class="sxs-lookup"><span data-stu-id="17a85-365">Otherwise, set to `false` to opt into the telemetry features (values `false`, `0`, or `no` accepted).</span></span> <span data-ttu-id="17a85-366">Jeśli nie zostanie ustawiona, wartość domyślna to `false` i aktywna jest funkcja telemetrii.</span><span class="sxs-lookup"><span data-stu-id="17a85-366">If not set, the default is `false` and the telemetry feature is active.</span></span>

---

## <a name="see-also"></a><span data-ttu-id="17a85-367">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="17a85-367">See also</span></span>

- [<span data-ttu-id="17a85-368">Pliki konfiguracji środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="17a85-368">Runtime Configuration Files</span></span>](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md)
- [<span data-ttu-id="17a85-369">Ustawienia konfiguracji środowiska uruchomieniowego .NET Core</span><span class="sxs-lookup"><span data-stu-id="17a85-369">.NET Core run-time configuration settings</span></span>](../run-time-config/index.md)
