---
title: dotnet, polecenie
description: Dowiedz się więcej o poleceniu dotnet (ogólnym sterowniku interfejsu wiersza polecenia .NET Core) i jego użyciu.
ms.date: 02/13/2020
ms.openlocfilehash: 9446808d7f23d762c7a3c8a58252664fc5dade5b
ms.sourcegitcommit: c91110ef6ee3fedb591f3d628dc17739c4a7071e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/15/2020
ms.locfileid: "81389598"
---
# <a name="dotnet-command"></a><span data-ttu-id="30efb-103">dotnet, polecenie</span><span class="sxs-lookup"><span data-stu-id="30efb-103">dotnet command</span></span>

<span data-ttu-id="30efb-104">**Ten artykuł dotyczy:** ✔️.NET Core 2.1 SDK i nowszych wersjach</span><span class="sxs-lookup"><span data-stu-id="30efb-104">**This article applies to:** ✔️ .NET Core 2.1 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="30efb-105">Nazwa</span><span class="sxs-lookup"><span data-stu-id="30efb-105">Name</span></span>

<span data-ttu-id="30efb-106">`dotnet`- Ogólny sterownik dla interfejsu wiersza polecenia .NET Core.</span><span class="sxs-lookup"><span data-stu-id="30efb-106">`dotnet` - The generic driver for the .NET Core CLI.</span></span>

## <a name="synopsis"></a><span data-ttu-id="30efb-107">Streszczenie</span><span class="sxs-lookup"><span data-stu-id="30efb-107">Synopsis</span></span>

<span data-ttu-id="30efb-108">Aby uzyskać informacje o dostępnych poleceniach i środowisku:</span><span class="sxs-lookup"><span data-stu-id="30efb-108">To get information about the available commands and the environment:</span></span>

```dotnetcli
dotnet [-h|--help] [--version] [--info]
    [--list-runtimes] [--list-sdks]
```

<span data-ttu-id="30efb-109">Aby uruchomić polecenie (wymaga instalacji SDK):</span><span class="sxs-lookup"><span data-stu-id="30efb-109">To run a command (requires SDK installation):</span></span>

```dotnetcli
dotnet <COMMAND> [-d|--diagnostics] [-h|--help] [--verbosity]
    [command-options] [arguments]
```

<span data-ttu-id="30efb-110">Aby uruchomić aplikację:</span><span class="sxs-lookup"><span data-stu-id="30efb-110">To run an application:</span></span>

```dotnetcli
dotnet [--additionalprobingpath] [--additional-deps]
    [--fx-version]  [--roll-forward]
    <PATH_TO_APPLICATION> [arguments]

dotnet exec [--additionalprobingpath] [--additional-deps]
    [--fx-version]  [--roll-forward]
    <PATH_TO_APPLICATION> [arguments]
```

<span data-ttu-id="30efb-111">`--roll-forward`jest dostępna od platformy .NET Core 3.x.</span><span class="sxs-lookup"><span data-stu-id="30efb-111">`--roll-forward` is available since .NET Core 3.x.</span></span> <span data-ttu-id="30efb-112">Użyj `--roll-forward-on-no-candidate-fx` dla .NET Core 2.x.</span><span class="sxs-lookup"><span data-stu-id="30efb-112">Use `--roll-forward-on-no-candidate-fx` for .NET Core 2.x.</span></span>

## <a name="description"></a><span data-ttu-id="30efb-113">Opis</span><span class="sxs-lookup"><span data-stu-id="30efb-113">Description</span></span>

<span data-ttu-id="30efb-114">Polecenie `dotnet` ma dwie funkcje:</span><span class="sxs-lookup"><span data-stu-id="30efb-114">The `dotnet` command has two functions:</span></span>

- <span data-ttu-id="30efb-115">Zapewnia polecenia do pracy z projektami .NET Core.</span><span class="sxs-lookup"><span data-stu-id="30efb-115">It provides commands for working with .NET Core projects.</span></span>

  <span data-ttu-id="30efb-116">Na przykład [`dotnet build`](dotnet-build.md) tworzy projekt.</span><span class="sxs-lookup"><span data-stu-id="30efb-116">For example, [`dotnet build`](dotnet-build.md) builds a project.</span></span> <span data-ttu-id="30efb-117">Każde polecenie definiuje własne opcje i argumenty.</span><span class="sxs-lookup"><span data-stu-id="30efb-117">Each command defines its own options and arguments.</span></span> <span data-ttu-id="30efb-118">Wszystkie polecenia obsługują `--help` opcję drukowania krótkiej dokumentacji dotyczącej sposobu korzystania z polecenia.</span><span class="sxs-lookup"><span data-stu-id="30efb-118">All commands support the `--help` option for printing out brief documentation about how to use the command.</span></span>

- <span data-ttu-id="30efb-119">Uruchamia aplikacje .NET Core.</span><span class="sxs-lookup"><span data-stu-id="30efb-119">It runs .NET Core applications.</span></span>

  <span data-ttu-id="30efb-120">Można określić ścieżkę `.dll` do pliku aplikacji, aby uruchomić aplikację.</span><span class="sxs-lookup"><span data-stu-id="30efb-120">You specify the path to an application `.dll` file to run the application.</span></span>  <span data-ttu-id="30efb-121">Aby uruchomić aplikację oznacza, aby znaleźć i wykonać punkt wejścia, `Main` który w przypadku aplikacji konsoli jest metodą.</span><span class="sxs-lookup"><span data-stu-id="30efb-121">To run the application means to find and execute the entry point, which in the case of console apps is the `Main` method.</span></span> <span data-ttu-id="30efb-122">Na przykład `dotnet myapp.dll` uruchamia `myapp` aplikację.</span><span class="sxs-lookup"><span data-stu-id="30efb-122">For example, `dotnet myapp.dll` runs the `myapp` application.</span></span> <span data-ttu-id="30efb-123">Zobacz [wdrożenie aplikacji .NET Core,](../deploying/index.md) aby dowiedzieć się więcej o opcjach wdrażania.</span><span class="sxs-lookup"><span data-stu-id="30efb-123">See [.NET Core application deployment](../deploying/index.md) to learn about deployment options.</span></span>

## <a name="options"></a><span data-ttu-id="30efb-124">Opcje</span><span class="sxs-lookup"><span data-stu-id="30efb-124">Options</span></span>

<span data-ttu-id="30efb-125">Różne opcje są `dotnet` dostępne dla siebie, do uruchamiania polecenia i uruchamiania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="30efb-125">Different options are available for `dotnet` by itself, for running a command, and for running an application.</span></span>

### <a name="options-for-dotnet-by-itself"></a><span data-ttu-id="30efb-126">Opcje dla dotnet sam</span><span class="sxs-lookup"><span data-stu-id="30efb-126">Options for dotnet by itself</span></span>

<span data-ttu-id="30efb-127">Następujące opcje są `dotnet` dla siebie.</span><span class="sxs-lookup"><span data-stu-id="30efb-127">The following options are for `dotnet` by itself.</span></span> <span data-ttu-id="30efb-128">Na przykład `dotnet --info`.</span><span class="sxs-lookup"><span data-stu-id="30efb-128">For example, `dotnet --info`.</span></span> <span data-ttu-id="30efb-129">Drukują informacje o środowisku.</span><span class="sxs-lookup"><span data-stu-id="30efb-129">They print out information about the environment.</span></span>

- **`--info`**

  <span data-ttu-id="30efb-130">Drukuje szczegółowe informacje o instalacji .NET Core i środowisku komputera, takich jak bieżący system operacyjny, i zatwierdza sha wersji .NET Core.</span><span class="sxs-lookup"><span data-stu-id="30efb-130">Prints out detailed information about a .NET Core installation and the machine environment, such as the current operating system, and commit SHA of the .NET Core version.</span></span>

- **`--version`**

  <span data-ttu-id="30efb-131">Drukuje używany plik.</span><span class="sxs-lookup"><span data-stu-id="30efb-131">Prints out the version of the .NET Core SDK in use.</span></span>

- **`--list-runtimes`**

  <span data-ttu-id="30efb-132">Drukuje listę zainstalowanych runtimes .NET Core.</span><span class="sxs-lookup"><span data-stu-id="30efb-132">Prints out a list of the installed .NET Core runtimes.</span></span> <span data-ttu-id="30efb-133">Wersja x86 SDK zawiera tylko środowiska wykonawcze x86, a wersja x64 SDK wyświetla tylko środowiska wykonawcze x64.</span><span class="sxs-lookup"><span data-stu-id="30efb-133">An x86 version of the SDK lists only x86 runtimes, and an x64 version of the SDK lists only x64 runtimes.</span></span>

- **`--list-sdks`**

  <span data-ttu-id="30efb-134">Drukuje listę zainstalowanych pakietów SDK .NET Core.</span><span class="sxs-lookup"><span data-stu-id="30efb-134">Prints out a list of the installed .NET Core SDKs.</span></span>

- **`-h|--help`**

  <span data-ttu-id="30efb-135">Drukuje listę dostępnych poleceń.</span><span class="sxs-lookup"><span data-stu-id="30efb-135">Prints out a list of available commands.</span></span>

### <a name="sdk-options-for-running-a-command"></a><span data-ttu-id="30efb-136">Opcje SDK do uruchamiania polecenia</span><span class="sxs-lookup"><span data-stu-id="30efb-136">SDK options for running a command</span></span>

<span data-ttu-id="30efb-137">Następujące opcje są `dotnet` dla z polecenia.</span><span class="sxs-lookup"><span data-stu-id="30efb-137">The following options are for `dotnet` with a command.</span></span> <span data-ttu-id="30efb-138">Na przykład `dotnet build --help`.</span><span class="sxs-lookup"><span data-stu-id="30efb-138">For example, `dotnet build --help`.</span></span>

- **`-d|--diagnostics`**

  <span data-ttu-id="30efb-139">Umożliwia wyjście diagnostyczne.</span><span class="sxs-lookup"><span data-stu-id="30efb-139">Enables diagnostic output.</span></span>

- **`-v|--verbosity <LEVEL>`**

  <span data-ttu-id="30efb-140">Ustawia poziom szczegółowości polecenia.</span><span class="sxs-lookup"><span data-stu-id="30efb-140">Sets the verbosity level of the command.</span></span> <span data-ttu-id="30efb-141">Dozwolone wartości `q[uiet]`to `m[inimal]` `n[ormal]`, `d[etailed]`, `diag[nostic]`, i .</span><span class="sxs-lookup"><span data-stu-id="30efb-141">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="30efb-142">Nie jest obsługiwany w każdym poleceniu.</span><span class="sxs-lookup"><span data-stu-id="30efb-142">Not supported in every command.</span></span> <span data-ttu-id="30efb-143">Zobacz określoną stronę polecenia, aby ustalić, czy ta opcja jest dostępna.</span><span class="sxs-lookup"><span data-stu-id="30efb-143">See specific command page to determine if this option is available.</span></span>

- **`-h|--help`**

  <span data-ttu-id="30efb-144">Drukuje dokumentację dla danego polecenia, na przykład `dotnet build --help`.</span><span class="sxs-lookup"><span data-stu-id="30efb-144">Prints out documentation for a given command, such as `dotnet build --help`.</span></span>

- **`command options`**

  <span data-ttu-id="30efb-145">Każde polecenie definiuje opcje specyficzne dla tego polecenia.</span><span class="sxs-lookup"><span data-stu-id="30efb-145">Each command defines options specific to that command.</span></span> <span data-ttu-id="30efb-146">Zobacz stronę poleceń, aby uzyskać listę dostępnych opcji.</span><span class="sxs-lookup"><span data-stu-id="30efb-146">See specific command page for a list of available options.</span></span>

### <a name="runtime-options"></a><span data-ttu-id="30efb-147">Opcje środowiska wykonawczego</span><span class="sxs-lookup"><span data-stu-id="30efb-147">Runtime options</span></span>

<span data-ttu-id="30efb-148">Następujące opcje są `dotnet` dostępne podczas uruchamiania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="30efb-148">The following options are available when `dotnet` runs an application.</span></span> <span data-ttu-id="30efb-149">Na przykład `dotnet myapp.dll --fx-version 3.1.1`.</span><span class="sxs-lookup"><span data-stu-id="30efb-149">For example, `dotnet myapp.dll --fx-version 3.1.1`.</span></span>

- **`--additionalprobingpath <PATH>`**

  <span data-ttu-id="30efb-150">Ścieżka zawierająca zasady sondowania i zestawy do sondowania.</span><span class="sxs-lookup"><span data-stu-id="30efb-150">Path containing probing policy and assemblies to probe.</span></span>

- **`--additional-deps <PATH>`**

  <span data-ttu-id="30efb-151">Ścieżka do dodatkowego pliku *deps.json.*</span><span class="sxs-lookup"><span data-stu-id="30efb-151">Path to an additional *.deps.json* file.</span></span> <span data-ttu-id="30efb-152">Plik *deps.json* zawiera listę zależności, zależności kompilacji i informacje o wersji używane do rozwiązywania konfliktów zestawu.</span><span class="sxs-lookup"><span data-stu-id="30efb-152">A *deps.json* file contains a list of dependencies, compilation dependencies, and version information used to address assembly conflicts.</span></span> <span data-ttu-id="30efb-153">Aby uzyskać więcej informacji, zobacz [Pliki konfiguracji środowiska wykonawczego](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md) w usłudze GitHub.</span><span class="sxs-lookup"><span data-stu-id="30efb-153">For more information, see [Runtime Configuration Files](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md) on GitHub.</span></span>

- **`--fx-version <VERSION>`**

  <span data-ttu-id="30efb-154">Wersja środowiska uruchomieniowego .NET Core do uruchomienia aplikacji.</span><span class="sxs-lookup"><span data-stu-id="30efb-154">Version of the .NET Core runtime to use to run the application.</span></span>

- **`--runtimeconfig`**

  <span data-ttu-id="30efb-155">Ścieżka do pliku *runtimeconfig.json.*</span><span class="sxs-lookup"><span data-stu-id="30efb-155">Path to a *runtimeconfig.json* file.</span></span> <span data-ttu-id="30efb-156">Plik *runtimeconfig.json* jest plikiem konfiguracyjnym zawierającym ustawienia czasu wykonywania.</span><span class="sxs-lookup"><span data-stu-id="30efb-156">A *runtimeconfig.json* file is a configuration file that contains run-time settings.</span></span> <span data-ttu-id="30efb-157">Aby uzyskać więcej informacji, zobacz [.NET Core ustawienia konfiguracji w czasie wykonywania](../run-time-config/index.md#runtimeconfigjson).</span><span class="sxs-lookup"><span data-stu-id="30efb-157">For more information, see [.NET Core run-time configuration settings](../run-time-config/index.md#runtimeconfigjson).</span></span>

- <span data-ttu-id="30efb-158">**`--roll-forward-on-no-candidate-fx <N>`\*\*\*\*Dostępne w pliku .NET Core 2.x SDK.**</span><span class="sxs-lookup"><span data-stu-id="30efb-158">**`--roll-forward-on-no-candidate-fx <N>`** **Available in .NET Core 2.x SDK.**</span></span>

  <span data-ttu-id="30efb-159">Definiuje zachowanie, gdy wymagana współużytkowana struktura nie jest dostępna.</span><span class="sxs-lookup"><span data-stu-id="30efb-159">Defines behavior when the required shared framework is not available.</span></span> <span data-ttu-id="30efb-160">`N`może to być:</span><span class="sxs-lookup"><span data-stu-id="30efb-160">`N` can be:</span></span>

  - <span data-ttu-id="30efb-161">`0`- Wyłącz nawet wersję pomocniczą rolki do przodu.</span><span class="sxs-lookup"><span data-stu-id="30efb-161">`0` - Disable even minor version roll forward.</span></span>
  - <span data-ttu-id="30efb-162">`1`- Roll forward w wersji pomocniczej, ale nie w wersji głównej.</span><span class="sxs-lookup"><span data-stu-id="30efb-162">`1` - Roll forward on minor version, but not on major version.</span></span> <span data-ttu-id="30efb-163">Jest to zachowanie domyślne.</span><span class="sxs-lookup"><span data-stu-id="30efb-163">This is the default behavior.</span></span>
  - <span data-ttu-id="30efb-164">`2`- Roll forward w wersji pomocniczej i głównej.</span><span class="sxs-lookup"><span data-stu-id="30efb-164">`2` - Roll forward on minor and major versions.</span></span>

   <span data-ttu-id="30efb-165">Aby uzyskać więcej informacji, zobacz [Przewij do przodu](../whats-new/dotnet-core-2-1.md#roll-forward).</span><span class="sxs-lookup"><span data-stu-id="30efb-165">For more information, see [Roll forward](../whats-new/dotnet-core-2-1.md#roll-forward).</span></span>

- <span data-ttu-id="30efb-166">**`--roll-forward <SETTING>`\*\*\*\*Dostępne począwszy od .NET Core SDK 3.0.**</span><span class="sxs-lookup"><span data-stu-id="30efb-166">**`--roll-forward <SETTING>`** **Available starting with .NET Core SDK 3.0.**</span></span>

  <span data-ttu-id="30efb-167">Określa sposób przekazywania do przodu jest stosowany do aplikacji.</span><span class="sxs-lookup"><span data-stu-id="30efb-167">Controls how roll forward is applied to the app.</span></span> <span data-ttu-id="30efb-168">`SETTING` Może to być jedna z następujących wartości.</span><span class="sxs-lookup"><span data-stu-id="30efb-168">The `SETTING` can be one of the following values.</span></span> <span data-ttu-id="30efb-169">Jeśli nie `Minor` zostanie określony, jest wartością domyślną.</span><span class="sxs-lookup"><span data-stu-id="30efb-169">If not specified, `Minor` is the default.</span></span>

  - <span data-ttu-id="30efb-170">`LatestPatch`- Przewiń do przodu do najwyższej wersji poprawki.</span><span class="sxs-lookup"><span data-stu-id="30efb-170">`LatestPatch` - Roll forward to the highest patch version.</span></span> <span data-ttu-id="30efb-171">Spowoduje to wyłączenie wersji pomocniczej do przodu.</span><span class="sxs-lookup"><span data-stu-id="30efb-171">This disables minor version roll forward.</span></span>
  - <span data-ttu-id="30efb-172">`Minor`- Przewiń do przodu do najniższej wyższej wersji pomocniczej, jeśli brakuje żądanej wersji pomocniczej.</span><span class="sxs-lookup"><span data-stu-id="30efb-172">`Minor` - Roll forward to the lowest higher minor version, if requested minor version is missing.</span></span> <span data-ttu-id="30efb-173">Jeśli żądana wersja pomocnicza jest obecna, używana jest zasada LatestPatch.</span><span class="sxs-lookup"><span data-stu-id="30efb-173">If the requested minor version is present, then the LatestPatch policy is used.</span></span>
  - <span data-ttu-id="30efb-174">`Major`- Przewiń do przodu do najniższej wyższej wersji głównej i najniższej wersji pomocniczej, jeśli brakuje żądanej wersji głównej.</span><span class="sxs-lookup"><span data-stu-id="30efb-174">`Major` - Roll forward to lowest higher major version, and lowest minor version, if requested major version is missing.</span></span> <span data-ttu-id="30efb-175">Jeśli żądana wersja główna jest obecny, a następnie drobne zasady są używane.</span><span class="sxs-lookup"><span data-stu-id="30efb-175">If the requested major version is present, then the Minor policy is used.</span></span>
  - <span data-ttu-id="30efb-176">`LatestMinor`- Przewiń do przodu do najwyższej wersji pomocniczej, nawet jeśli wymagana wersja pomocnicza jest obecna.</span><span class="sxs-lookup"><span data-stu-id="30efb-176">`LatestMinor` - Roll forward to highest minor version, even if requested minor version is present.</span></span> <span data-ttu-id="30efb-177">Przeznaczone do scenariuszy hostingu składników.</span><span class="sxs-lookup"><span data-stu-id="30efb-177">Intended for component hosting scenarios.</span></span>
  - <span data-ttu-id="30efb-178">`LatestMajor`- Roll forward do najwyższej wersji głównej i najwyższej wersji pomocniczej, nawet jeśli wymagane major jest obecny.</span><span class="sxs-lookup"><span data-stu-id="30efb-178">`LatestMajor` - Roll forward to highest major and highest minor version, even if requested major is present.</span></span> <span data-ttu-id="30efb-179">Przeznaczone do scenariuszy hostingu składników.</span><span class="sxs-lookup"><span data-stu-id="30efb-179">Intended for component hosting scenarios.</span></span>
  - <span data-ttu-id="30efb-180">`Disable`- Nie tocz do przodu.</span><span class="sxs-lookup"><span data-stu-id="30efb-180">`Disable` - Don't roll forward.</span></span> <span data-ttu-id="30efb-181">Tylko powiązanie z określoną wersją.</span><span class="sxs-lookup"><span data-stu-id="30efb-181">Only bind to specified version.</span></span> <span data-ttu-id="30efb-182">Ta zasada nie jest zalecana do ogólnego użytku, ponieważ wyłącza możliwość przekazywania do najnowszych poprawek.</span><span class="sxs-lookup"><span data-stu-id="30efb-182">This policy isn't recommended for general use because it disables the ability to roll forward to the latest patches.</span></span> <span data-ttu-id="30efb-183">Ta wartość jest zalecana tylko do testowania.</span><span class="sxs-lookup"><span data-stu-id="30efb-183">This value is only recommended for testing.</span></span>

<span data-ttu-id="30efb-184">Z wyjątkiem `Disable`, wszystkie ustawienia będą korzystać z najwyższej dostępnej wersji poprawki.</span><span class="sxs-lookup"><span data-stu-id="30efb-184">With the exception of `Disable`, all settings will use the highest available patch version.</span></span>

<span data-ttu-id="30efb-185">Zachowanie przewijania do przodu można również skonfigurować we właściwości pliku projektu, właściwości pliku konfiguracji w czasie wykonywania i zmiennej środowiskowej.</span><span class="sxs-lookup"><span data-stu-id="30efb-185">Roll forward behavior can also be configured in a project file property, a run-time configuration file property, and an environment variable.</span></span> <span data-ttu-id="30efb-186">Aby uzyskać więcej informacji, zobacz [Główne wersje runtime roll do przodu](../whats-new/dotnet-core-3-0.md#major-version-runtime-roll-forward).</span><span class="sxs-lookup"><span data-stu-id="30efb-186">For more information, see [Major-version runtime roll forward](../whats-new/dotnet-core-3-0.md#major-version-runtime-roll-forward).</span></span>

## <a name="dotnet-commands"></a><span data-ttu-id="30efb-187">Polecenia dotnet</span><span class="sxs-lookup"><span data-stu-id="30efb-187">dotnet commands</span></span>

### <a name="general"></a><span data-ttu-id="30efb-188">Ogólne</span><span class="sxs-lookup"><span data-stu-id="30efb-188">General</span></span>

| <span data-ttu-id="30efb-189">Polecenie</span><span class="sxs-lookup"><span data-stu-id="30efb-189">Command</span></span>                                       | <span data-ttu-id="30efb-190">Funkcja</span><span class="sxs-lookup"><span data-stu-id="30efb-190">Function</span></span>                                                            |
| --------------------------------------------- | ------------------------------------------------------------------- |
| [<span data-ttu-id="30efb-191">dotnet build</span><span class="sxs-lookup"><span data-stu-id="30efb-191">dotnet build</span></span>](dotnet-build.md)               | <span data-ttu-id="30efb-192">Tworzy aplikację .NET Core.</span><span class="sxs-lookup"><span data-stu-id="30efb-192">Builds a .NET Core application.</span></span>                                     |
| [<span data-ttu-id="30efb-193">dotnet build-server</span><span class="sxs-lookup"><span data-stu-id="30efb-193">dotnet build-server</span></span>](dotnet-build-server.md) | <span data-ttu-id="30efb-194">Współdziała z serwerami uruchomionymi przez kompilację.</span><span class="sxs-lookup"><span data-stu-id="30efb-194">Interacts with servers started by a build.</span></span>                          |
| [<span data-ttu-id="30efb-195">dotnet clean</span><span class="sxs-lookup"><span data-stu-id="30efb-195">dotnet clean</span></span>](dotnet-clean.md)               | <span data-ttu-id="30efb-196">Czyste wyjścia kompilacji.</span><span class="sxs-lookup"><span data-stu-id="30efb-196">Clean build outputs.</span></span>                                                |
| [<span data-ttu-id="30efb-197">dotnet help</span><span class="sxs-lookup"><span data-stu-id="30efb-197">dotnet help</span></span>](dotnet-help.md)                 | <span data-ttu-id="30efb-198">Pokazuje bardziej szczegółową dokumentację dla polecenia.</span><span class="sxs-lookup"><span data-stu-id="30efb-198">Shows more detailed documentation online for the command.</span></span>           |
| [<span data-ttu-id="30efb-199">dotnet migrate</span><span class="sxs-lookup"><span data-stu-id="30efb-199">dotnet migrate</span></span>](dotnet-migrate.md)           | <span data-ttu-id="30efb-200">Migruje prawidłowy projekt w wersji zapoznawczej 2 do projektu .NET Core SDK 1.0.</span><span class="sxs-lookup"><span data-stu-id="30efb-200">Migrates a valid Preview 2 project to a .NET Core SDK 1.0 project.</span></span>  |
| [<span data-ttu-id="30efb-201">dotnet msbuild</span><span class="sxs-lookup"><span data-stu-id="30efb-201">dotnet msbuild</span></span>](dotnet-msbuild.md)           | <span data-ttu-id="30efb-202">Zapewnia dostęp do wiersza polecenia MSBuild.</span><span class="sxs-lookup"><span data-stu-id="30efb-202">Provides access to the MSBuild command line.</span></span>                        |
| [<span data-ttu-id="30efb-203">dotnet new</span><span class="sxs-lookup"><span data-stu-id="30efb-203">dotnet new</span></span>](dotnet-new.md)                   | <span data-ttu-id="30efb-204">Inicjuje projekt C# lub F# dla danego szablonu.</span><span class="sxs-lookup"><span data-stu-id="30efb-204">Initializes a C# or F# project for a given template.</span></span>                |
| [<span data-ttu-id="30efb-205">dotnet pack</span><span class="sxs-lookup"><span data-stu-id="30efb-205">dotnet pack</span></span>](dotnet-pack.md)                 | <span data-ttu-id="30efb-206">Tworzy pakiet NuGet kodu.</span><span class="sxs-lookup"><span data-stu-id="30efb-206">Creates a NuGet package of your code.</span></span>                               |
| [<span data-ttu-id="30efb-207">dotnet publish</span><span class="sxs-lookup"><span data-stu-id="30efb-207">dotnet publish</span></span>](dotnet-publish.md)           | <span data-ttu-id="30efb-208">Publikuje aplikację zależną od struktury .NET lub niezależną.</span><span class="sxs-lookup"><span data-stu-id="30efb-208">Publishes a .NET framework-dependent or self-contained application.</span></span> |
| [<span data-ttu-id="30efb-209">dotnet restore</span><span class="sxs-lookup"><span data-stu-id="30efb-209">dotnet restore</span></span>](dotnet-restore.md)           | <span data-ttu-id="30efb-210">Przywraca zależności dla danej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="30efb-210">Restores the dependencies for a given application.</span></span>                  |
| [<span data-ttu-id="30efb-211">dotnet run</span><span class="sxs-lookup"><span data-stu-id="30efb-211">dotnet run</span></span>](dotnet-run.md)                   | <span data-ttu-id="30efb-212">Uruchamia aplikację ze źródła.</span><span class="sxs-lookup"><span data-stu-id="30efb-212">Runs the application from source.</span></span>                                   |
| [<span data-ttu-id="30efb-213">dotnet sln</span><span class="sxs-lookup"><span data-stu-id="30efb-213">dotnet sln</span></span>](dotnet-sln.md)                   | <span data-ttu-id="30efb-214">Opcje dodawania, usuwania i listy projektów w pliku rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="30efb-214">Options to add, remove, and list projects in a solution file.</span></span>       |
| [<span data-ttu-id="30efb-215">dotnet store</span><span class="sxs-lookup"><span data-stu-id="30efb-215">dotnet store</span></span>](dotnet-store.md)               | <span data-ttu-id="30efb-216">Przechowuje zestawy w magazynie pakietów środowiska wykonawczego.</span><span class="sxs-lookup"><span data-stu-id="30efb-216">Stores assemblies in the runtime package store.</span></span>                     |
| [<span data-ttu-id="30efb-217">dotnet test</span><span class="sxs-lookup"><span data-stu-id="30efb-217">dotnet test</span></span>](dotnet-test.md)                 | <span data-ttu-id="30efb-218">Uruchamia testy przy użyciu testowej próby.</span><span class="sxs-lookup"><span data-stu-id="30efb-218">Runs tests using a test runner.</span></span>                                     |

### <a name="project-references"></a><span data-ttu-id="30efb-219">Odwołania projektu</span><span class="sxs-lookup"><span data-stu-id="30efb-219">Project references</span></span>

<span data-ttu-id="30efb-220">Polecenie</span><span class="sxs-lookup"><span data-stu-id="30efb-220">Command</span></span> | <span data-ttu-id="30efb-221">Funkcja</span><span class="sxs-lookup"><span data-stu-id="30efb-221">Function</span></span>
--- | ---
[<span data-ttu-id="30efb-222">dotnet add reference</span><span class="sxs-lookup"><span data-stu-id="30efb-222">dotnet add reference</span></span>](dotnet-add-reference.md) | <span data-ttu-id="30efb-223">Dodaje odwołanie do projektu.</span><span class="sxs-lookup"><span data-stu-id="30efb-223">Adds a project reference.</span></span>
[<span data-ttu-id="30efb-224">dotnet list reference</span><span class="sxs-lookup"><span data-stu-id="30efb-224">dotnet list reference</span></span>](dotnet-list-reference.md) | <span data-ttu-id="30efb-225">Wyświetla listę odwołań do projektu.</span><span class="sxs-lookup"><span data-stu-id="30efb-225">Lists project references.</span></span>
[<span data-ttu-id="30efb-226">dotnet remove reference</span><span class="sxs-lookup"><span data-stu-id="30efb-226">dotnet remove reference</span></span>](dotnet-remove-reference.md) | <span data-ttu-id="30efb-227">Usuwa odwołanie do projektu.</span><span class="sxs-lookup"><span data-stu-id="30efb-227">Removes a project reference.</span></span>

### <a name="nuget-packages"></a><span data-ttu-id="30efb-228">Pakiety NuGet</span><span class="sxs-lookup"><span data-stu-id="30efb-228">NuGet packages</span></span>

<span data-ttu-id="30efb-229">Polecenie</span><span class="sxs-lookup"><span data-stu-id="30efb-229">Command</span></span> | <span data-ttu-id="30efb-230">Funkcja</span><span class="sxs-lookup"><span data-stu-id="30efb-230">Function</span></span>
--- | ---
[<span data-ttu-id="30efb-231">dotnet add package</span><span class="sxs-lookup"><span data-stu-id="30efb-231">dotnet add package</span></span>](dotnet-add-package.md) | <span data-ttu-id="30efb-232">Dodaje pakiet NuGet.</span><span class="sxs-lookup"><span data-stu-id="30efb-232">Adds a NuGet package.</span></span>
[<span data-ttu-id="30efb-233">dotnet remove package</span><span class="sxs-lookup"><span data-stu-id="30efb-233">dotnet remove package</span></span>](dotnet-remove-package.md) | <span data-ttu-id="30efb-234">Usuwa pakiet NuGet.</span><span class="sxs-lookup"><span data-stu-id="30efb-234">Removes a NuGet package.</span></span>

### <a name="nuget-commands"></a><span data-ttu-id="30efb-235">Polecenia NuGet</span><span class="sxs-lookup"><span data-stu-id="30efb-235">NuGet commands</span></span>

<span data-ttu-id="30efb-236">Polecenie</span><span class="sxs-lookup"><span data-stu-id="30efb-236">Command</span></span> | <span data-ttu-id="30efb-237">Funkcja</span><span class="sxs-lookup"><span data-stu-id="30efb-237">Function</span></span>
--- | ---
[<span data-ttu-id="30efb-238">dotnet nuget delete</span><span class="sxs-lookup"><span data-stu-id="30efb-238">dotnet nuget delete</span></span>](dotnet-nuget-delete.md) | <span data-ttu-id="30efb-239">Usuwa lub usuwa listę pakiet z serwera.</span><span class="sxs-lookup"><span data-stu-id="30efb-239">Deletes or unlists a package from the server.</span></span>
[<span data-ttu-id="30efb-240">dotnet nuget push</span><span class="sxs-lookup"><span data-stu-id="30efb-240">dotnet nuget push</span></span>](dotnet-nuget-push.md) | <span data-ttu-id="30efb-241">Wypycha pakiet do serwera i publikuje go.</span><span class="sxs-lookup"><span data-stu-id="30efb-241">Pushes a package to the server and publishes it.</span></span>
[<span data-ttu-id="30efb-242">dotnet nuget locals</span><span class="sxs-lookup"><span data-stu-id="30efb-242">dotnet nuget locals</span></span>](dotnet-nuget-locals.md) | <span data-ttu-id="30efb-243">Czyści lub wyświetla lokalne zasoby NuGet, takie jak pamięć podręczna żądań http, tymczasowa pamięć podręczna lub folder pakietów globalnych dla całej maszyny.</span><span class="sxs-lookup"><span data-stu-id="30efb-243">Clears or lists local NuGet resources such as http-request cache, temporary cache, or machine-wide global packages folder.</span></span>
[<span data-ttu-id="30efb-244">dotnet nuget add source</span><span class="sxs-lookup"><span data-stu-id="30efb-244">dotnet nuget add source</span></span>](dotnet-nuget-add-source.md) | <span data-ttu-id="30efb-245">Dodaje źródło NuGet.</span><span class="sxs-lookup"><span data-stu-id="30efb-245">Adds a NuGet source.</span></span>
[<span data-ttu-id="30efb-246">dotnet nuget disable source</span><span class="sxs-lookup"><span data-stu-id="30efb-246">dotnet nuget disable source</span></span>](dotnet-nuget-disable-source.md) | <span data-ttu-id="30efb-247">Wyłącza źródło NuGet.</span><span class="sxs-lookup"><span data-stu-id="30efb-247">Disables a NuGet source.</span></span>
[<span data-ttu-id="30efb-248">dotnet nuget enable source</span><span class="sxs-lookup"><span data-stu-id="30efb-248">dotnet nuget enable source</span></span>](dotnet-nuget-enable-source.md) | <span data-ttu-id="30efb-249">Włącza źródło NuGet.</span><span class="sxs-lookup"><span data-stu-id="30efb-249">Enables a NuGet source.</span></span>
[<span data-ttu-id="30efb-250">dotnet nuget list source</span><span class="sxs-lookup"><span data-stu-id="30efb-250">dotnet nuget list source</span></span>](dotnet-nuget-list-source.md) | <span data-ttu-id="30efb-251">Wyświetla listę wszystkich skonfigurowanych źródeł NuGet.</span><span class="sxs-lookup"><span data-stu-id="30efb-251">Lists all configured NuGet sources.</span></span>
[<span data-ttu-id="30efb-252">dotnet nuget remove source</span><span class="sxs-lookup"><span data-stu-id="30efb-252">dotnet nuget remove source</span></span>](dotnet-nuget-remove-source.md) | <span data-ttu-id="30efb-253">Usuwa źródło NuGet.</span><span class="sxs-lookup"><span data-stu-id="30efb-253">Removes a NuGet source.</span></span>
[<span data-ttu-id="30efb-254">dotnet nuget update source</span><span class="sxs-lookup"><span data-stu-id="30efb-254">dotnet nuget update source</span></span>](dotnet-nuget-update-source.md) | <span data-ttu-id="30efb-255">Aktualizuje źródło NuGet.</span><span class="sxs-lookup"><span data-stu-id="30efb-255">Updates a NuGet source.</span></span>

### <a name="global-tool-path-and-local-tools-commands"></a><span data-ttu-id="30efb-256">Polecenia narzędzi globalnych, ścieżki narzędzi i narzędzi lokalnych</span><span class="sxs-lookup"><span data-stu-id="30efb-256">Global, tool-path, and local tools commands</span></span>

<span data-ttu-id="30efb-257">Narzędzia są aplikacje konsoli, które są instalowane z pakietów NuGet i są wywoływane z wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="30efb-257">Tools are console applications that are installed from NuGet packages and are invoked from the command prompt.</span></span> <span data-ttu-id="30efb-258">Możesz samodzielnie napisać narzędzia lub zainstalować narzędzia napisane przez osoby trzecie.</span><span class="sxs-lookup"><span data-stu-id="30efb-258">You can write tools yourself or install tools written by third parties.</span></span> <span data-ttu-id="30efb-259">Narzędzia są również nazywane narzędziami globalnymi, narzędziami ścieżki narzędzi i narzędziami lokalnymi.</span><span class="sxs-lookup"><span data-stu-id="30efb-259">Tools are also known as global tools, tool-path tools, and local tools.</span></span> <span data-ttu-id="30efb-260">Aby uzyskać więcej informacji, zobacz [omówienie narzędzi .NET Core](global-tools.md).</span><span class="sxs-lookup"><span data-stu-id="30efb-260">For more information, see [.NET Core tools overview](global-tools.md).</span></span> <span data-ttu-id="30efb-261">Globalne i narzędzia ścieżki narzędzi są dostępne począwszy od .NET Core SDK 2.1.</span><span class="sxs-lookup"><span data-stu-id="30efb-261">Global and tool-path tools are available starting with .NET Core SDK 2.1.</span></span> <span data-ttu-id="30efb-262">Narzędzia lokalne są dostępne począwszy od .NET Core SDK 3.0.</span><span class="sxs-lookup"><span data-stu-id="30efb-262">Local tools are available starting with .NET Core SDK 3.0.</span></span>

<span data-ttu-id="30efb-263">Polecenie</span><span class="sxs-lookup"><span data-stu-id="30efb-263">Command</span></span> | <span data-ttu-id="30efb-264">Funkcja</span><span class="sxs-lookup"><span data-stu-id="30efb-264">Function</span></span>
--- | ---
[<span data-ttu-id="30efb-265">dotnet tool install</span><span class="sxs-lookup"><span data-stu-id="30efb-265">dotnet tool install</span></span>](dotnet-tool-install.md) | <span data-ttu-id="30efb-266">Instaluje narzędzie na komputerze.</span><span class="sxs-lookup"><span data-stu-id="30efb-266">Installs a tool on your machine.</span></span>
[<span data-ttu-id="30efb-267">dotnet tool list</span><span class="sxs-lookup"><span data-stu-id="30efb-267">dotnet tool list</span></span>](dotnet-tool-list.md) | <span data-ttu-id="30efb-268">Wyświetla listę wszystkich narzędzi globalnych, ścieżki narzędzi lub narzędzi lokalnych aktualnie zainstalowanych na komputerze.</span><span class="sxs-lookup"><span data-stu-id="30efb-268">Lists all global, tool-path, or local tools currently installed on your machine.</span></span>
[<span data-ttu-id="30efb-269">dotnet tool uninstall</span><span class="sxs-lookup"><span data-stu-id="30efb-269">dotnet tool uninstall</span></span>](dotnet-tool-uninstall.md) | <span data-ttu-id="30efb-270">Odinstalowuje narzędzie z komputera.</span><span class="sxs-lookup"><span data-stu-id="30efb-270">Uninstalls a tool from your machine.</span></span>
[<span data-ttu-id="30efb-271">dotnet tool update</span><span class="sxs-lookup"><span data-stu-id="30efb-271">dotnet tool update</span></span>](dotnet-tool-update.md) | <span data-ttu-id="30efb-272">Aktualizuje narzędzie zainstalowane na komputerze.</span><span class="sxs-lookup"><span data-stu-id="30efb-272">Updates a tool that is installed on your machine.</span></span>

### <a name="additional-tools"></a><span data-ttu-id="30efb-273">Dodatkowe narzędzia</span><span class="sxs-lookup"><span data-stu-id="30efb-273">Additional tools</span></span>

<span data-ttu-id="30efb-274">Począwszy od zestawu .NET Core SDK 2.1.300, wiele narzędzi, `DotnetCliToolReference` które były dostępne tylko na podstawie projektu, są teraz dostępne jako część zestawu .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="30efb-274">Starting with .NET Core SDK 2.1.300, a number of tools that were available only on a per project basis using `DotnetCliToolReference` are now available as part of the .NET Core SDK.</span></span> <span data-ttu-id="30efb-275">Narzędzia te są wymienione w poniższej tabeli:</span><span class="sxs-lookup"><span data-stu-id="30efb-275">These tools are listed in the following table:</span></span>

| <span data-ttu-id="30efb-276">Narzędzie</span><span class="sxs-lookup"><span data-stu-id="30efb-276">Tool</span></span>                                              | <span data-ttu-id="30efb-277">Funkcja</span><span class="sxs-lookup"><span data-stu-id="30efb-277">Function</span></span>                                                     |
| ------------------------------------------------- | ------------------------------------------------------------ |
| <span data-ttu-id="30efb-278">dev-certs</span><span class="sxs-lookup"><span data-stu-id="30efb-278">dev-certs</span></span>                                         | <span data-ttu-id="30efb-279">Tworzy certyfikaty deweloperów i zarządza nimi.</span><span class="sxs-lookup"><span data-stu-id="30efb-279">Creates and manages development certificates.</span></span>                |
| [<span data-ttu-id="30efb-280">Ef</span><span class="sxs-lookup"><span data-stu-id="30efb-280">ef</span></span>](/ef/core/miscellaneous/cli/dotnet)           | <span data-ttu-id="30efb-281">Narzędzia wiersza polecenia Core entity framework.</span><span class="sxs-lookup"><span data-stu-id="30efb-281">Entity Framework Core command-line tools.</span></span>                    |
| <span data-ttu-id="30efb-282">sql-cache</span><span class="sxs-lookup"><span data-stu-id="30efb-282">sql-cache</span></span>                                         | <span data-ttu-id="30efb-283">Narzędzia wiersza polecenia pamięci podręcznej programu SQL Server.</span><span class="sxs-lookup"><span data-stu-id="30efb-283">SQL Server cache command-line tools.</span></span>                         |
| [<span data-ttu-id="30efb-284">tajemnice użytkownika</span><span class="sxs-lookup"><span data-stu-id="30efb-284">user-secrets</span></span>](/aspnet/core/security/app-secrets) | <span data-ttu-id="30efb-285">Zarządza wpisami tajnymi użytkowników deweloperów.</span><span class="sxs-lookup"><span data-stu-id="30efb-285">Manages development user secrets.</span></span>                            |
| [<span data-ttu-id="30efb-286">Oglądać</span><span class="sxs-lookup"><span data-stu-id="30efb-286">watch</span></span>](/aspnet/core/tutorials/dotnet-watch)      | <span data-ttu-id="30efb-287">Uruchamia obserwatora plików, który uruchamia polecenie po zmianie plików.</span><span class="sxs-lookup"><span data-stu-id="30efb-287">Starts a file watcher that runs a command when files change.</span></span> |

<span data-ttu-id="30efb-288">Aby uzyskać więcej informacji `dotnet <tool-name> --help`o każdym narzędziu, wpisz .</span><span class="sxs-lookup"><span data-stu-id="30efb-288">For more information about each tool, type `dotnet <tool-name> --help`.</span></span>

## <a name="examples"></a><span data-ttu-id="30efb-289">Przykłady</span><span class="sxs-lookup"><span data-stu-id="30efb-289">Examples</span></span>

<span data-ttu-id="30efb-290">Utwórz nową aplikację konsoli .NET Core:</span><span class="sxs-lookup"><span data-stu-id="30efb-290">Create a new .NET Core console application:</span></span>

```dotnetcli
dotnet new console
```

<span data-ttu-id="30efb-291">Tworzenie projektu i jego zależności w danym katalogu:</span><span class="sxs-lookup"><span data-stu-id="30efb-291">Build a project and its dependencies in a given directory:</span></span>

```dotnetcli
dotnet build
```

<span data-ttu-id="30efb-292">Uruchamianie aplikacji:</span><span class="sxs-lookup"><span data-stu-id="30efb-292">Run an application:</span></span>

```dotnetcli
dotnet myapp.dll
```

## <a name="environment-variables"></a><span data-ttu-id="30efb-293">Zmienne środowiskowe</span><span class="sxs-lookup"><span data-stu-id="30efb-293">Environment variables</span></span>

- <span data-ttu-id="30efb-294">`DOTNET_ROOT`, `DOTNET_ROOT(x86)`</span><span class="sxs-lookup"><span data-stu-id="30efb-294">`DOTNET_ROOT`, `DOTNET_ROOT(x86)`</span></span>

  <span data-ttu-id="30efb-295">Określa lokalizację środowiska uruchomień .NET Core, jeśli nie są zainstalowane w lokalizacji domyślnej.</span><span class="sxs-lookup"><span data-stu-id="30efb-295">Specifies the location of the .NET Core runtimes, if they are not installed in the default location.</span></span> <span data-ttu-id="30efb-296">Domyślną lokalizacją `C:\Program Files\dotnet`w systemie Windows jest .</span><span class="sxs-lookup"><span data-stu-id="30efb-296">The default location on Windows is `C:\Program Files\dotnet`.</span></span> <span data-ttu-id="30efb-297">Domyślną lokalizacją w systemach Linux i macOS jest `/usr/share/dotnet`.</span><span class="sxs-lookup"><span data-stu-id="30efb-297">The default location on Linux and macOS is `/usr/share/dotnet`.</span></span> <span data-ttu-id="30efb-298">Ta zmienna środowiskowa jest używana tylko podczas uruchamiania aplikacji za pośrednictwem wygenerowanych plików wykonywalnych (apphosts).</span><span class="sxs-lookup"><span data-stu-id="30efb-298">This environment variable is used only when running apps via generated executables (apphosts).</span></span> <span data-ttu-id="30efb-299">`DOTNET_ROOT(x86)`jest używany podczas uruchamiania 32-bitowego pliku wykonywalnego na 64-bitowym os.</span><span class="sxs-lookup"><span data-stu-id="30efb-299">`DOTNET_ROOT(x86)` is used instead when running a 32-bit executable on a 64-bit OS.</span></span>

- `DOTNET_PACKAGES`

  <span data-ttu-id="30efb-300">Folder pakietów globalnych.</span><span class="sxs-lookup"><span data-stu-id="30efb-300">The global packages folder.</span></span> <span data-ttu-id="30efb-301">Jeśli nie jest ustawiona, domyślnie jest to `~/.nuget/packages` w systemie Unix lub `%userprofile%\.nuget\packages` Windows.</span><span class="sxs-lookup"><span data-stu-id="30efb-301">If not set, it defaults to `~/.nuget/packages` on Unix or `%userprofile%\.nuget\packages` on Windows.</span></span>

- `DOTNET_SERVICING`

  <span data-ttu-id="30efb-302">Określa lokalizację indeksu obsługi do użycia przez hosta udostępnionego podczas ładowania środowiska wykonawczego.</span><span class="sxs-lookup"><span data-stu-id="30efb-302">Specifies the location of the servicing index to use by the shared host when loading the runtime.</span></span>

- `DOTNET_NOLOGO`

  <span data-ttu-id="30efb-303">Określa, czy komunikaty powitalne .NET Core i telemetryczne są wyświetlane przy pierwszym uruchomieniu.</span><span class="sxs-lookup"><span data-stu-id="30efb-303">Specifies whether .NET Core welcome and telemetry messages are displayed on first run.</span></span> <span data-ttu-id="30efb-304">Ustaw, `true` aby wyciszyć `true`te `1`komunikaty `yes` (wartości , `false` lub zaakceptowane) lub ustawić, aby zezwolić (wartości `false`, `0`, lub `no` akceptowane).</span><span class="sxs-lookup"><span data-stu-id="30efb-304">Set to `true` to mute these messages (values `true`, `1`, or `yes` accepted) or set to `false` to allow (values `false`, `0`, or `no` accepted).</span></span> <span data-ttu-id="30efb-305">Jeśli nie jest ustawiona, domyślna jest `false` i komunikaty będą wyświetlane przy pierwszym uruchomieniu.</span><span class="sxs-lookup"><span data-stu-id="30efb-305">If not set, the default is `false` and the messages will be displayed on first run.</span></span> <span data-ttu-id="30efb-306">Należy zauważyć, że ta flaga `DOTNET_CLI_TELEMETRY_OPTOUT` nie ma wpływu na dane telemetryczne (zobacz rezygnacji z wysyłania danych telemetrycznych).</span><span class="sxs-lookup"><span data-stu-id="30efb-306">Note that this flag has no effect on telemetry (see `DOTNET_CLI_TELEMETRY_OPTOUT` for opting out of sending telemetry).</span></span>

- `DOTNET_CLI_TELEMETRY_OPTOUT`

  <span data-ttu-id="30efb-307">Określa, czy dane dotyczące użycia narzędzi .NET Core są zbierane i wysyłane do firmy Microsoft.</span><span class="sxs-lookup"><span data-stu-id="30efb-307">Specifies whether data about the .NET Core tools usage is collected and sent to Microsoft.</span></span> <span data-ttu-id="30efb-308">Ustaw `true` opcję rezygnacji z funkcji telemetrii (wartości `true`lub `1` `yes` zaakceptowane).</span><span class="sxs-lookup"><span data-stu-id="30efb-308">Set to `true` to opt-out of the telemetry feature (values `true`, `1`, or `yes` accepted).</span></span> <span data-ttu-id="30efb-309">W przeciwnym `false` razie należy ustawić opcję wyboru `false` `0`funkcji `no` telemetrycznych (wartości lub zaakceptowanych).</span><span class="sxs-lookup"><span data-stu-id="30efb-309">Otherwise, set to `false` to opt into the telemetry features (values `false`, `0`, or `no` accepted).</span></span> <span data-ttu-id="30efb-310">Jeśli nie jest ustawiona, ustawieniem domyślnym jest `false` funkcja telemetrii.</span><span class="sxs-lookup"><span data-stu-id="30efb-310">If not set, the default is `false` and the telemetry feature is active.</span></span>

- `DOTNET_MULTILEVEL_LOOKUP`

  <span data-ttu-id="30efb-311">Określa, czy środowisko uruchomieniowe .NET Core, współużytkowana struktura lub SDK są rozpoznawane z lokalizacji globalnej.</span><span class="sxs-lookup"><span data-stu-id="30efb-311">Specifies whether .NET Core runtime, shared framework, or SDK are resolved from the global location.</span></span> <span data-ttu-id="30efb-312">Jeśli nie jest ustawiona, domyślnie `true`jest to 1 (logiczne ).</span><span class="sxs-lookup"><span data-stu-id="30efb-312">If not set, it defaults to 1 (logical `true`).</span></span> <span data-ttu-id="30efb-313">Ustaw wartość 0 `false`(logiczna), aby nie rozwiązać problemu z lokalizacji globalnej i mieć izolowane instalacje .NET Core.</span><span class="sxs-lookup"><span data-stu-id="30efb-313">Set to 0 (logical `false`) to not resolve from the global location and have isolated .NET Core installations.</span></span> <span data-ttu-id="30efb-314">Aby uzyskać więcej informacji na temat wyszukiwania wielopoziomowego, zobacz [Wielopoziomowe wyszukiwanie SharedFX](https://github.com/dotnet/core-setup/blob/master/Documentation/design-docs/multilevel-sharedfx-lookup.md).</span><span class="sxs-lookup"><span data-stu-id="30efb-314">For more information about multi-level lookup, see [Multi-level SharedFX Lookup](https://github.com/dotnet/core-setup/blob/master/Documentation/design-docs/multilevel-sharedfx-lookup.md).</span></span>

- <span data-ttu-id="30efb-315">`DOTNET_ROLL_FORWARD`**Dostępne począwszy od .NET Core 3.x SDK.**</span><span class="sxs-lookup"><span data-stu-id="30efb-315">`DOTNET_ROLL_FORWARD` **Available starting with .NET Core 3.x SDK.**</span></span>

  <span data-ttu-id="30efb-316">Określa zachowanie przewijania do przodu.</span><span class="sxs-lookup"><span data-stu-id="30efb-316">Determines roll forward behavior.</span></span> <span data-ttu-id="30efb-317">Aby uzyskać więcej `--roll-forward` informacji, zobacz opcję wcześniej w tym artykule.</span><span class="sxs-lookup"><span data-stu-id="30efb-317">For more information, see the `--roll-forward` option earlier in this article.</span></span>

- <span data-ttu-id="30efb-318">`DOTNET_ROLL_FORWARD_ON_NO_CANDIDATE_FX`**Dostępne w pliku .NET Core 2.x SDK.**</span><span class="sxs-lookup"><span data-stu-id="30efb-318">`DOTNET_ROLL_FORWARD_ON_NO_CANDIDATE_FX` **Available in .NET Core 2.x SDK.**</span></span>

  <span data-ttu-id="30efb-319">Wyłącza wersję pomocniczą do `0`przodu, jeśli jest ustawiona na .</span><span class="sxs-lookup"><span data-stu-id="30efb-319">Disables minor version roll forward, if set to `0`.</span></span> <span data-ttu-id="30efb-320">Aby uzyskać więcej informacji, zobacz [Przewij do przodu](../whats-new/dotnet-core-2-1.md#roll-forward).</span><span class="sxs-lookup"><span data-stu-id="30efb-320">For more information, see [Roll forward](../whats-new/dotnet-core-2-1.md#roll-forward).</span></span>

- `DOTNET_CLI_UI_LANGUAGE`

  <span data-ttu-id="30efb-321">Ustawia język interfejsu użytkownika interfejsu wiersza polecenia `en-us`przy użyciu wartości ustawień regionalnych, takich jak .</span><span class="sxs-lookup"><span data-stu-id="30efb-321">Sets the language of the CLI UI using a locale value such as `en-us`.</span></span> <span data-ttu-id="30efb-322">Obsługiwane wartości są takie same jak w programie Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="30efb-322">The supported values are the same as for Visual Studio.</span></span> <span data-ttu-id="30efb-323">Aby uzyskać więcej informacji, zobacz sekcję dotyczącą zmieniania języka instalatora w [dokumentacji instalacji programu Visual Studio](https://docs.microsoft.com/visualstudio/install/install-visual-studio?view=vs-2019).</span><span class="sxs-lookup"><span data-stu-id="30efb-323">For more information, see the section on changing the installer language in the [Visual Studio installation documentation](https://docs.microsoft.com/visualstudio/install/install-visual-studio?view=vs-2019).</span></span> <span data-ttu-id="30efb-324">Zasady Menedżera zasobów .NET mają zastosowanie, więc nie trzeba&mdash;wybierać dopasowania dokładnego, które można również wybrać elementy podrzędne w `CultureInfo` drzewie.</span><span class="sxs-lookup"><span data-stu-id="30efb-324">The .NET resource manager rules apply, so you don't have to pick an exact match&mdash;you can also pick descendants in the `CultureInfo` tree.</span></span> <span data-ttu-id="30efb-325">Na przykład, jeśli ustawisz go na `fr-CA`, `fr` CLI znajdzie i użyje tłumaczeń.</span><span class="sxs-lookup"><span data-stu-id="30efb-325">For example, if you set it to `fr-CA`, the CLI will find and use the `fr` translations.</span></span> <span data-ttu-id="30efb-326">Jeśli ustawisz go na język, który nie jest obsługiwany, cli powróci do języka angielskiego.</span><span class="sxs-lookup"><span data-stu-id="30efb-326">If you set it to a language that is not supported, the CLI falls back to English.</span></span>

- `DOTNET_DISABLE_GUI_ERRORS`

  <span data-ttu-id="30efb-327">W przypadku generowanych plików wykonywalnych z funkcją GUI — wyłącza okno dialogowe, które zwykle jest wyświetlane dla niektórych klas błędów.</span><span class="sxs-lookup"><span data-stu-id="30efb-327">For GUI-enabled generated executables - disables dialog popup, which normally shows for certain classes of errors.</span></span> <span data-ttu-id="30efb-328">To tylko zapisuje `stderr` i kończy się w tych przypadkach.</span><span class="sxs-lookup"><span data-stu-id="30efb-328">It only writes to `stderr` and exits in those cases.</span></span>
  
- `DOTNET_ADDITIONAL_DEPS`

  <span data-ttu-id="30efb-329">Odpowiednik opcji `--additional-deps`interfejsu wiersza polecenia .</span><span class="sxs-lookup"><span data-stu-id="30efb-329">Equivalent to CLI option `--additional-deps`.</span></span>

- `DOTNET_RUNTIME_ID`

  <span data-ttu-id="30efb-330">Zastępuje wykryty identyfikator RID.</span><span class="sxs-lookup"><span data-stu-id="30efb-330">Overrides the detected RID.</span></span>

- `DOTNET_SHARED_STORE`

  <span data-ttu-id="30efb-331">Lokalizacja "magazynu udostępnionego", do którego rozdzielczość zestawu powraca w niektórych przypadkach.</span><span class="sxs-lookup"><span data-stu-id="30efb-331">Location of the "shared store" which assembly resolution falls back to in some cases.</span></span>

- `DOTNET_STARTUP_HOOKS`

  <span data-ttu-id="30efb-332">Lista zestawów do załadowania i wykonania haków startowych.</span><span class="sxs-lookup"><span data-stu-id="30efb-332">List of assemblies to load and execute startup hooks from.</span></span>

- <span data-ttu-id="30efb-333">`COREHOST_TRACE`, `COREHOST_TRACEFILE`, `COREHOST_TRACE_VERBOSITY`</span><span class="sxs-lookup"><span data-stu-id="30efb-333">`COREHOST_TRACE`, `COREHOST_TRACEFILE`, `COREHOST_TRACE_VERBOSITY`</span></span>

  <span data-ttu-id="30efb-334">Steruje śledzeniem diagnostyki ze składników `dotnet.exe` `hostfxr`hostingu, takich jak , i `hostpolicy`.</span><span class="sxs-lookup"><span data-stu-id="30efb-334">Controls diagnostics tracing from the hosting components, such as `dotnet.exe`, `hostfxr`, and `hostpolicy`.</span></span>

## <a name="see-also"></a><span data-ttu-id="30efb-335">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="30efb-335">See also</span></span>

- [<span data-ttu-id="30efb-336">Pliki konfiguracji środowiska wykonawczego</span><span class="sxs-lookup"><span data-stu-id="30efb-336">Runtime Configuration Files</span></span>](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md)
- [<span data-ttu-id="30efb-337">Ustawienia konfiguracji w czasie wykonywania rdzenia .NET</span><span class="sxs-lookup"><span data-stu-id="30efb-337">.NET Core run-time configuration settings</span></span>](../run-time-config/index.md)
