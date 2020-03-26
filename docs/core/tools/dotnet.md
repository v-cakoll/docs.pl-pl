---
title: dotnet, polecenie
description: Dowiedz się więcej o poleceniu dotnet (ogólnym sterowniku interfejsu wiersza polecenia .NET Core) i jego użyciu.
ms.date: 02/13/2020
ms.openlocfilehash: 8692d419afd528bf49e1dc7dc1a7a5fd698b363b
ms.sourcegitcommit: 07123a475af89b6da5bb6cc51ea40ab1e8a488f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80134074"
---
# <a name="dotnet-command"></a><span data-ttu-id="c336b-103">dotnet, polecenie</span><span class="sxs-lookup"><span data-stu-id="c336b-103">dotnet command</span></span>

<span data-ttu-id="c336b-104">**Ten artykuł dotyczy:** ✔️.NET Core 2.1 SDK i nowszych wersjach</span><span class="sxs-lookup"><span data-stu-id="c336b-104">**This article applies to:** ✔️ .NET Core 2.1 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="c336b-105">Nazwa</span><span class="sxs-lookup"><span data-stu-id="c336b-105">Name</span></span>

<span data-ttu-id="c336b-106">`dotnet`- Ogólny sterownik dla interfejsu wiersza polecenia .NET Core.</span><span class="sxs-lookup"><span data-stu-id="c336b-106">`dotnet` - The generic driver for the .NET Core CLI.</span></span>

## <a name="synopsis"></a><span data-ttu-id="c336b-107">Streszczenie</span><span class="sxs-lookup"><span data-stu-id="c336b-107">Synopsis</span></span>

<span data-ttu-id="c336b-108">Aby uzyskać informacje o dostępnych poleceniach i środowisku:</span><span class="sxs-lookup"><span data-stu-id="c336b-108">To get information about the available commands and the environment:</span></span>

```dotnetcli
dotnet [-h|--help] [--version] [--info]
    [--list-runtimes] [--list-sdks]
```

<span data-ttu-id="c336b-109">Aby uruchomić polecenie (wymaga instalacji SDK):</span><span class="sxs-lookup"><span data-stu-id="c336b-109">To run a command (requires SDK installation):</span></span>

```dotnetcli
dotnet <COMMAND> [-d|--diagnostics] [-h|--help] [--verbosity]
    [command-options] [arguments]
```

<span data-ttu-id="c336b-110">Aby uruchomić aplikację:</span><span class="sxs-lookup"><span data-stu-id="c336b-110">To run an application:</span></span>

```dotnetcli
dotnet [--additionalprobingpath] [--additional-deps]
    [--fx-version]  [--roll-forward]
    <PATH_TO_APPLICATION> [arguments]

dotnet exec [--additionalprobingpath] [--additional-deps]
    [--fx-version]  [--roll-forward]
    <PATH_TO_APPLICATION> [arguments]
```

<span data-ttu-id="c336b-111">`--roll-forward`jest dostępna od platformy .NET Core 3.x.</span><span class="sxs-lookup"><span data-stu-id="c336b-111">`--roll-forward` is available since .NET Core 3.x.</span></span> <span data-ttu-id="c336b-112">Użyj `--roll-forward-on-no-candidate-fx` dla .NET Core 2.x.</span><span class="sxs-lookup"><span data-stu-id="c336b-112">Use `--roll-forward-on-no-candidate-fx` for .NET Core 2.x.</span></span>

## <a name="description"></a><span data-ttu-id="c336b-113">Opis</span><span class="sxs-lookup"><span data-stu-id="c336b-113">Description</span></span>

<span data-ttu-id="c336b-114">Polecenie `dotnet` ma dwie funkcje:</span><span class="sxs-lookup"><span data-stu-id="c336b-114">The `dotnet` command has two functions:</span></span>

- <span data-ttu-id="c336b-115">Zapewnia polecenia do pracy z projektami .NET Core.</span><span class="sxs-lookup"><span data-stu-id="c336b-115">It provides commands for working with .NET Core projects.</span></span>

  <span data-ttu-id="c336b-116">Na przykład [`dotnet build`](dotnet-build.md) tworzy projekt.</span><span class="sxs-lookup"><span data-stu-id="c336b-116">For example, [`dotnet build`](dotnet-build.md) builds a project.</span></span> <span data-ttu-id="c336b-117">Każde polecenie definiuje własne opcje i argumenty.</span><span class="sxs-lookup"><span data-stu-id="c336b-117">Each command defines its own options and arguments.</span></span> <span data-ttu-id="c336b-118">Wszystkie polecenia obsługują `--help` opcję drukowania krótkiej dokumentacji dotyczącej sposobu korzystania z polecenia.</span><span class="sxs-lookup"><span data-stu-id="c336b-118">All commands support the `--help` option for printing out brief documentation about how to use the command.</span></span>

- <span data-ttu-id="c336b-119">Uruchamia aplikacje .NET Core.</span><span class="sxs-lookup"><span data-stu-id="c336b-119">It runs .NET Core applications.</span></span>

  <span data-ttu-id="c336b-120">Można określić ścieżkę `.dll` do pliku aplikacji, aby uruchomić aplikację.</span><span class="sxs-lookup"><span data-stu-id="c336b-120">You specify the path to an application `.dll` file to run the application.</span></span> <span data-ttu-id="c336b-121">Na przykład `dotnet myapp.dll` uruchamia `myapp` aplikację.</span><span class="sxs-lookup"><span data-stu-id="c336b-121">For example, `dotnet myapp.dll` runs the `myapp` application.</span></span> <span data-ttu-id="c336b-122">Zobacz [wdrożenie aplikacji .NET Core,](../deploying/index.md) aby dowiedzieć się więcej o opcjach wdrażania.</span><span class="sxs-lookup"><span data-stu-id="c336b-122">See [.NET Core application deployment](../deploying/index.md) to learn about deployment options.</span></span>

## <a name="options"></a><span data-ttu-id="c336b-123">Opcje</span><span class="sxs-lookup"><span data-stu-id="c336b-123">Options</span></span>

<span data-ttu-id="c336b-124">Różne opcje są `dotnet` dostępne dla siebie, do uruchamiania polecenia i uruchamiania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="c336b-124">Different options are available for `dotnet` by itself, for running a command, and for running an application.</span></span>

### <a name="options-for-dotnet-by-itself"></a><span data-ttu-id="c336b-125">Opcje dla dotnet sam</span><span class="sxs-lookup"><span data-stu-id="c336b-125">Options for dotnet by itself</span></span>

<span data-ttu-id="c336b-126">Następujące opcje są `dotnet` dla siebie.</span><span class="sxs-lookup"><span data-stu-id="c336b-126">The following options are for `dotnet` by itself.</span></span> <span data-ttu-id="c336b-127">Na przykład `dotnet --info`.</span><span class="sxs-lookup"><span data-stu-id="c336b-127">For example, `dotnet --info`.</span></span> <span data-ttu-id="c336b-128">Drukują informacje o środowisku.</span><span class="sxs-lookup"><span data-stu-id="c336b-128">They print out information about the environment.</span></span>

- **`--info`**

  <span data-ttu-id="c336b-129">Drukuje szczegółowe informacje o instalacji .NET Core i środowisku komputera, takich jak bieżący system operacyjny, i zatwierdza sha wersji .NET Core.</span><span class="sxs-lookup"><span data-stu-id="c336b-129">Prints out detailed information about a .NET Core installation and the machine environment, such as the current operating system, and commit SHA of the .NET Core version.</span></span>

- **`--version`**

  <span data-ttu-id="c336b-130">Drukuje używany plik.</span><span class="sxs-lookup"><span data-stu-id="c336b-130">Prints out the version of the .NET Core SDK in use.</span></span>

- **`--list-runtimes`**

  <span data-ttu-id="c336b-131">Drukuje listę zainstalowanych runtimes .NET Core.</span><span class="sxs-lookup"><span data-stu-id="c336b-131">Prints out a list of the installed .NET Core runtimes.</span></span>

- **`--list-sdks`**

  <span data-ttu-id="c336b-132">Drukuje listę zainstalowanych pakietów SDK .NET Core.</span><span class="sxs-lookup"><span data-stu-id="c336b-132">Prints out a list of the installed .NET Core SDKs.</span></span>

- **`-h|--help`**

  <span data-ttu-id="c336b-133">Drukuje listę dostępnych poleceń.</span><span class="sxs-lookup"><span data-stu-id="c336b-133">Prints out a list of available commands.</span></span>

### <a name="sdk-options-for-running-a-command"></a><span data-ttu-id="c336b-134">Opcje SDK do uruchamiania polecenia</span><span class="sxs-lookup"><span data-stu-id="c336b-134">SDK options for running a command</span></span>

<span data-ttu-id="c336b-135">Następujące opcje są `dotnet` dla z polecenia.</span><span class="sxs-lookup"><span data-stu-id="c336b-135">The following options are for `dotnet` with a command.</span></span> <span data-ttu-id="c336b-136">Na przykład `dotnet build --help`.</span><span class="sxs-lookup"><span data-stu-id="c336b-136">For example, `dotnet build --help`.</span></span>

- **`-d|--diagnostics`**

  <span data-ttu-id="c336b-137">Umożliwia wyjście diagnostyczne.</span><span class="sxs-lookup"><span data-stu-id="c336b-137">Enables diagnostic output.</span></span>

- **`-v|--verbosity <LEVEL>`**

  <span data-ttu-id="c336b-138">Ustawia poziom szczegółowości polecenia.</span><span class="sxs-lookup"><span data-stu-id="c336b-138">Sets the verbosity level of the command.</span></span> <span data-ttu-id="c336b-139">Dozwolone wartości `q[uiet]`to `m[inimal]` `n[ormal]`, `d[etailed]`, `diag[nostic]`, i .</span><span class="sxs-lookup"><span data-stu-id="c336b-139">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="c336b-140">Nie jest obsługiwany w każdym poleceniu.</span><span class="sxs-lookup"><span data-stu-id="c336b-140">Not supported in every command.</span></span> <span data-ttu-id="c336b-141">Zobacz określoną stronę polecenia, aby ustalić, czy ta opcja jest dostępna.</span><span class="sxs-lookup"><span data-stu-id="c336b-141">See specific command page to determine if this option is available.</span></span>

- **`-h|--help`**

  <span data-ttu-id="c336b-142">Drukuje dokumentację dla danego polecenia, na przykład `dotnet build --help`.</span><span class="sxs-lookup"><span data-stu-id="c336b-142">Prints out documentation for a given command, such as `dotnet build --help`.</span></span>

- **`command options`**

  <span data-ttu-id="c336b-143">Każde polecenie definiuje opcje specyficzne dla tego polecenia.</span><span class="sxs-lookup"><span data-stu-id="c336b-143">Each command defines options specific to that command.</span></span> <span data-ttu-id="c336b-144">Zobacz stronę poleceń, aby uzyskać listę dostępnych opcji.</span><span class="sxs-lookup"><span data-stu-id="c336b-144">See specific command page for a list of available options.</span></span>

### <a name="runtime-options"></a><span data-ttu-id="c336b-145">Opcje środowiska wykonawczego</span><span class="sxs-lookup"><span data-stu-id="c336b-145">Runtime options</span></span>

<span data-ttu-id="c336b-146">Następujące opcje są `dotnet` dostępne podczas uruchamiania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="c336b-146">The following options are available when `dotnet` runs an application.</span></span> <span data-ttu-id="c336b-147">Na przykład `dotnet myapp.dll --fx-version 3.1.1`.</span><span class="sxs-lookup"><span data-stu-id="c336b-147">For example, `dotnet myapp.dll --fx-version 3.1.1`.</span></span>

- **`--additionalprobingpath <PATH>`**

  <span data-ttu-id="c336b-148">Ścieżka zawierająca zasady sondowania i zestawy do sondowania.</span><span class="sxs-lookup"><span data-stu-id="c336b-148">Path containing probing policy and assemblies to probe.</span></span>

- **`--additional-deps <PATH>`**

  <span data-ttu-id="c336b-149">Ścieżka do dodatkowego pliku *deps.json.*</span><span class="sxs-lookup"><span data-stu-id="c336b-149">Path to an additional *.deps.json* file.</span></span> <span data-ttu-id="c336b-150">Plik *deps.json* zawiera listę zależności, zależności kompilacji i informacje o wersji używane do rozwiązywania konfliktów zestawu.</span><span class="sxs-lookup"><span data-stu-id="c336b-150">A *deps.json* file contains a list of dependencies, compilation dependencies, and version information used to address assembly conflicts.</span></span> <span data-ttu-id="c336b-151">Aby uzyskać więcej informacji, zobacz [Pliki konfiguracji środowiska wykonawczego](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md) w usłudze GitHub.</span><span class="sxs-lookup"><span data-stu-id="c336b-151">For more information, see [Runtime Configuration Files](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md) on GitHub.</span></span>

- **`--fx-version <VERSION>`**

  <span data-ttu-id="c336b-152">Wersja środowiska uruchomieniowego .NET Core do uruchomienia aplikacji.</span><span class="sxs-lookup"><span data-stu-id="c336b-152">Version of the .NET Core runtime to use to run the application.</span></span>

- **`--runtimeconfig`**

  <span data-ttu-id="c336b-153">Ścieżka do pliku *runtimeconfig.json.*</span><span class="sxs-lookup"><span data-stu-id="c336b-153">Path to a *runtimeconfig.json* file.</span></span> <span data-ttu-id="c336b-154">Plik *runtimeconfig.json* jest plikiem konfiguracyjnym zawierającym ustawienia czasu wykonywania.</span><span class="sxs-lookup"><span data-stu-id="c336b-154">A *runtimeconfig.json* file is a configuration file that contains run-time settings.</span></span> <span data-ttu-id="c336b-155">Aby uzyskać więcej informacji, zobacz [.NET Core ustawienia konfiguracji w czasie wykonywania](../run-time-config/index.md#runtimeconfigjson).</span><span class="sxs-lookup"><span data-stu-id="c336b-155">For more information, see [.NET Core run-time configuration settings](../run-time-config/index.md#runtimeconfigjson).</span></span>

- <span data-ttu-id="c336b-156">**`--roll-forward-on-no-candidate-fx <N>`\*\*\*\*Dostępne w pliku .NET Core 2.x SDK.**</span><span class="sxs-lookup"><span data-stu-id="c336b-156">**`--roll-forward-on-no-candidate-fx <N>`** **Available in .NET Core 2.x SDK.**</span></span>

  <span data-ttu-id="c336b-157">Definiuje zachowanie, gdy wymagana współużytkowana struktura nie jest dostępna.</span><span class="sxs-lookup"><span data-stu-id="c336b-157">Defines behavior when the required shared framework is not available.</span></span> <span data-ttu-id="c336b-158">`N`może to być:</span><span class="sxs-lookup"><span data-stu-id="c336b-158">`N` can be:</span></span>

  - <span data-ttu-id="c336b-159">`0`- Wyłącz nawet wersję pomocniczą rolki do przodu.</span><span class="sxs-lookup"><span data-stu-id="c336b-159">`0` - Disable even minor version roll forward.</span></span>
  - <span data-ttu-id="c336b-160">`1`- Roll forward w wersji pomocniczej, ale nie w wersji głównej.</span><span class="sxs-lookup"><span data-stu-id="c336b-160">`1` - Roll forward on minor version, but not on major version.</span></span> <span data-ttu-id="c336b-161">Jest to zachowanie domyślne.</span><span class="sxs-lookup"><span data-stu-id="c336b-161">This is the default behavior.</span></span>
  - <span data-ttu-id="c336b-162">`2`- Roll forward w wersji pomocniczej i głównej.</span><span class="sxs-lookup"><span data-stu-id="c336b-162">`2` - Roll forward on minor and major versions.</span></span>

   <span data-ttu-id="c336b-163">Aby uzyskać więcej informacji, zobacz [Przewij do przodu](../whats-new/dotnet-core-2-1.md#roll-forward).</span><span class="sxs-lookup"><span data-stu-id="c336b-163">For more information, see [Roll forward](../whats-new/dotnet-core-2-1.md#roll-forward).</span></span>

- <span data-ttu-id="c336b-164">**`--roll-forward <SETTING>`\*\*\*\*Dostępne począwszy od .NET Core SDK 3.0.**</span><span class="sxs-lookup"><span data-stu-id="c336b-164">**`--roll-forward <SETTING>`** **Available starting with .NET Core SDK 3.0.**</span></span>

  <span data-ttu-id="c336b-165">Określa sposób przekazywania do przodu jest stosowany do aplikacji.</span><span class="sxs-lookup"><span data-stu-id="c336b-165">Controls how roll forward is applied to the app.</span></span> <span data-ttu-id="c336b-166">`SETTING` Może to być jedna z następujących wartości.</span><span class="sxs-lookup"><span data-stu-id="c336b-166">The `SETTING` can be one of the following values.</span></span> <span data-ttu-id="c336b-167">Jeśli nie `Minor` zostanie określony, jest wartością domyślną.</span><span class="sxs-lookup"><span data-stu-id="c336b-167">If not specified, `Minor` is the default.</span></span>

  - <span data-ttu-id="c336b-168">`LatestPatch`- Przewiń do przodu do najwyższej wersji poprawki.</span><span class="sxs-lookup"><span data-stu-id="c336b-168">`LatestPatch` - Roll forward to the highest patch version.</span></span> <span data-ttu-id="c336b-169">Spowoduje to wyłączenie wersji pomocniczej do przodu.</span><span class="sxs-lookup"><span data-stu-id="c336b-169">This disables minor version roll forward.</span></span>
  - <span data-ttu-id="c336b-170">`Minor`- Przewiń do przodu do najniższej wyższej wersji pomocniczej, jeśli brakuje żądanej wersji pomocniczej.</span><span class="sxs-lookup"><span data-stu-id="c336b-170">`Minor` - Roll forward to the lowest higher minor version, if requested minor version is missing.</span></span> <span data-ttu-id="c336b-171">Jeśli żądana wersja pomocnicza jest obecna, używana jest zasada LatestPatch.</span><span class="sxs-lookup"><span data-stu-id="c336b-171">If the requested minor version is present, then the LatestPatch policy is used.</span></span>
  - <span data-ttu-id="c336b-172">`Major`- Przewiń do przodu do najniższej wyższej wersji głównej i najniższej wersji pomocniczej, jeśli brakuje żądanej wersji głównej.</span><span class="sxs-lookup"><span data-stu-id="c336b-172">`Major` - Roll forward to lowest higher major version, and lowest minor version, if requested major version is missing.</span></span> <span data-ttu-id="c336b-173">Jeśli żądana wersja główna jest obecny, a następnie drobne zasady są używane.</span><span class="sxs-lookup"><span data-stu-id="c336b-173">If the requested major version is present, then the Minor policy is used.</span></span>
  - <span data-ttu-id="c336b-174">`LatestMinor`- Przewiń do przodu do najwyższej wersji pomocniczej, nawet jeśli wymagana wersja pomocnicza jest obecna.</span><span class="sxs-lookup"><span data-stu-id="c336b-174">`LatestMinor` - Roll forward to highest minor version, even if requested minor version is present.</span></span> <span data-ttu-id="c336b-175">Przeznaczone do scenariuszy hostingu składników.</span><span class="sxs-lookup"><span data-stu-id="c336b-175">Intended for component hosting scenarios.</span></span>
  - <span data-ttu-id="c336b-176">`LatestMajor`- Roll forward do najwyższej wersji głównej i najwyższej wersji pomocniczej, nawet jeśli wymagane major jest obecny.</span><span class="sxs-lookup"><span data-stu-id="c336b-176">`LatestMajor` - Roll forward to highest major and highest minor version, even if requested major is present.</span></span> <span data-ttu-id="c336b-177">Przeznaczone do scenariuszy hostingu składników.</span><span class="sxs-lookup"><span data-stu-id="c336b-177">Intended for component hosting scenarios.</span></span>
  - <span data-ttu-id="c336b-178">`Disable`- Nie tocz do przodu.</span><span class="sxs-lookup"><span data-stu-id="c336b-178">`Disable` - Don't roll forward.</span></span> <span data-ttu-id="c336b-179">Tylko powiązanie z określoną wersją.</span><span class="sxs-lookup"><span data-stu-id="c336b-179">Only bind to specified version.</span></span> <span data-ttu-id="c336b-180">Ta zasada nie jest zalecana do ogólnego użytku, ponieważ wyłącza możliwość przekazywania do najnowszych poprawek.</span><span class="sxs-lookup"><span data-stu-id="c336b-180">This policy isn't recommended for general use because it disables the ability to roll forward to the latest patches.</span></span> <span data-ttu-id="c336b-181">Ta wartość jest zalecana tylko do testowania.</span><span class="sxs-lookup"><span data-stu-id="c336b-181">This value is only recommended for testing.</span></span>

<span data-ttu-id="c336b-182">Z wyjątkiem `Disable`, wszystkie ustawienia będą korzystać z najwyższej dostępnej wersji poprawki.</span><span class="sxs-lookup"><span data-stu-id="c336b-182">With the exception of `Disable`, all settings will use the highest available patch version.</span></span>

<span data-ttu-id="c336b-183">Zachowanie przewijania do przodu można również skonfigurować we właściwości pliku projektu, właściwości pliku konfiguracji w czasie wykonywania i zmiennej środowiskowej.</span><span class="sxs-lookup"><span data-stu-id="c336b-183">Roll forward behavior can also be configured in a project file property, a run-time configuration file property, and an environment variable.</span></span> <span data-ttu-id="c336b-184">Aby uzyskać więcej informacji, zobacz [Główne wersje runtime roll do przodu](../whats-new/dotnet-core-3-0.md#major-version-runtime-roll-forward).</span><span class="sxs-lookup"><span data-stu-id="c336b-184">For more information, see [Major-version runtime roll forward](../whats-new/dotnet-core-3-0.md#major-version-runtime-roll-forward).</span></span>

## <a name="dotnet-commands"></a><span data-ttu-id="c336b-185">Polecenia dotnet</span><span class="sxs-lookup"><span data-stu-id="c336b-185">dotnet commands</span></span>

### <a name="general"></a><span data-ttu-id="c336b-186">Ogólne</span><span class="sxs-lookup"><span data-stu-id="c336b-186">General</span></span>

| <span data-ttu-id="c336b-187">Polecenie</span><span class="sxs-lookup"><span data-stu-id="c336b-187">Command</span></span>                                       | <span data-ttu-id="c336b-188">Funkcja</span><span class="sxs-lookup"><span data-stu-id="c336b-188">Function</span></span>                                                            |
| --------------------------------------------- | ------------------------------------------------------------------- |
| [<span data-ttu-id="c336b-189">dotnet build</span><span class="sxs-lookup"><span data-stu-id="c336b-189">dotnet build</span></span>](dotnet-build.md)               | <span data-ttu-id="c336b-190">Tworzy aplikację .NET Core.</span><span class="sxs-lookup"><span data-stu-id="c336b-190">Builds a .NET Core application.</span></span>                                     |
| [<span data-ttu-id="c336b-191">dotnet build-server</span><span class="sxs-lookup"><span data-stu-id="c336b-191">dotnet build-server</span></span>](dotnet-build-server.md) | <span data-ttu-id="c336b-192">Współdziała z serwerami uruchomionymi przez kompilację.</span><span class="sxs-lookup"><span data-stu-id="c336b-192">Interacts with servers started by a build.</span></span>                          |
| [<span data-ttu-id="c336b-193">dotnet clean</span><span class="sxs-lookup"><span data-stu-id="c336b-193">dotnet clean</span></span>](dotnet-clean.md)               | <span data-ttu-id="c336b-194">Czyste wyjścia kompilacji.</span><span class="sxs-lookup"><span data-stu-id="c336b-194">Clean build outputs.</span></span>                                                |
| [<span data-ttu-id="c336b-195">dotnet help</span><span class="sxs-lookup"><span data-stu-id="c336b-195">dotnet help</span></span>](dotnet-help.md)                 | <span data-ttu-id="c336b-196">Pokazuje bardziej szczegółową dokumentację dla polecenia.</span><span class="sxs-lookup"><span data-stu-id="c336b-196">Shows more detailed documentation online for the command.</span></span>           |
| [<span data-ttu-id="c336b-197">dotnet migrate</span><span class="sxs-lookup"><span data-stu-id="c336b-197">dotnet migrate</span></span>](dotnet-migrate.md)           | <span data-ttu-id="c336b-198">Migruje prawidłowy projekt w wersji zapoznawczej 2 do projektu .NET Core SDK 1.0.</span><span class="sxs-lookup"><span data-stu-id="c336b-198">Migrates a valid Preview 2 project to a .NET Core SDK 1.0 project.</span></span>  |
| [<span data-ttu-id="c336b-199">dotnet msbuild</span><span class="sxs-lookup"><span data-stu-id="c336b-199">dotnet msbuild</span></span>](dotnet-msbuild.md)           | <span data-ttu-id="c336b-200">Zapewnia dostęp do wiersza polecenia MSBuild.</span><span class="sxs-lookup"><span data-stu-id="c336b-200">Provides access to the MSBuild command line.</span></span>                        |
| [<span data-ttu-id="c336b-201">dotnet new</span><span class="sxs-lookup"><span data-stu-id="c336b-201">dotnet new</span></span>](dotnet-new.md)                   | <span data-ttu-id="c336b-202">Inicjuje projekt C# lub F# dla danego szablonu.</span><span class="sxs-lookup"><span data-stu-id="c336b-202">Initializes a C# or F# project for a given template.</span></span>                |
| [<span data-ttu-id="c336b-203">dotnet pack</span><span class="sxs-lookup"><span data-stu-id="c336b-203">dotnet pack</span></span>](dotnet-pack.md)                 | <span data-ttu-id="c336b-204">Tworzy pakiet NuGet kodu.</span><span class="sxs-lookup"><span data-stu-id="c336b-204">Creates a NuGet package of your code.</span></span>                               |
| [<span data-ttu-id="c336b-205">dotnet publish</span><span class="sxs-lookup"><span data-stu-id="c336b-205">dotnet publish</span></span>](dotnet-publish.md)           | <span data-ttu-id="c336b-206">Publikuje aplikację zależną od struktury .NET lub niezależną.</span><span class="sxs-lookup"><span data-stu-id="c336b-206">Publishes a .NET framework-dependent or self-contained application.</span></span> |
| [<span data-ttu-id="c336b-207">dotnet restore</span><span class="sxs-lookup"><span data-stu-id="c336b-207">dotnet restore</span></span>](dotnet-restore.md)           | <span data-ttu-id="c336b-208">Przywraca zależności dla danej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="c336b-208">Restores the dependencies for a given application.</span></span>                  |
| [<span data-ttu-id="c336b-209">dotnet run</span><span class="sxs-lookup"><span data-stu-id="c336b-209">dotnet run</span></span>](dotnet-run.md)                   | <span data-ttu-id="c336b-210">Uruchamia aplikację ze źródła.</span><span class="sxs-lookup"><span data-stu-id="c336b-210">Runs the application from source.</span></span>                                   |
| [<span data-ttu-id="c336b-211">dotnet sln</span><span class="sxs-lookup"><span data-stu-id="c336b-211">dotnet sln</span></span>](dotnet-sln.md)                   | <span data-ttu-id="c336b-212">Opcje dodawania, usuwania i listy projektów w pliku rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="c336b-212">Options to add, remove, and list projects in a solution file.</span></span>       |
| [<span data-ttu-id="c336b-213">dotnet store</span><span class="sxs-lookup"><span data-stu-id="c336b-213">dotnet store</span></span>](dotnet-store.md)               | <span data-ttu-id="c336b-214">Przechowuje zestawy w magazynie pakietów środowiska wykonawczego.</span><span class="sxs-lookup"><span data-stu-id="c336b-214">Stores assemblies in the runtime package store.</span></span>                     |
| [<span data-ttu-id="c336b-215">dotnet test</span><span class="sxs-lookup"><span data-stu-id="c336b-215">dotnet test</span></span>](dotnet-test.md)                 | <span data-ttu-id="c336b-216">Uruchamia testy przy użyciu testowej próby.</span><span class="sxs-lookup"><span data-stu-id="c336b-216">Runs tests using a test runner.</span></span>                                     |

### <a name="project-references"></a><span data-ttu-id="c336b-217">Odwołania projektu</span><span class="sxs-lookup"><span data-stu-id="c336b-217">Project references</span></span>

<span data-ttu-id="c336b-218">Polecenie</span><span class="sxs-lookup"><span data-stu-id="c336b-218">Command</span></span> | <span data-ttu-id="c336b-219">Funkcja</span><span class="sxs-lookup"><span data-stu-id="c336b-219">Function</span></span>
--- | ---
[<span data-ttu-id="c336b-220">dotnet add reference</span><span class="sxs-lookup"><span data-stu-id="c336b-220">dotnet add reference</span></span>](dotnet-add-reference.md) | <span data-ttu-id="c336b-221">Dodaje odwołanie do projektu.</span><span class="sxs-lookup"><span data-stu-id="c336b-221">Adds a project reference.</span></span>
[<span data-ttu-id="c336b-222">dotnet list reference</span><span class="sxs-lookup"><span data-stu-id="c336b-222">dotnet list reference</span></span>](dotnet-list-reference.md) | <span data-ttu-id="c336b-223">Wyświetla listę odwołań do projektu.</span><span class="sxs-lookup"><span data-stu-id="c336b-223">Lists project references.</span></span>
[<span data-ttu-id="c336b-224">dotnet remove reference</span><span class="sxs-lookup"><span data-stu-id="c336b-224">dotnet remove reference</span></span>](dotnet-remove-reference.md) | <span data-ttu-id="c336b-225">Usuwa odwołanie do projektu.</span><span class="sxs-lookup"><span data-stu-id="c336b-225">Removes a project reference.</span></span>

### <a name="nuget-packages"></a><span data-ttu-id="c336b-226">Pakiety NuGet</span><span class="sxs-lookup"><span data-stu-id="c336b-226">NuGet packages</span></span>

<span data-ttu-id="c336b-227">Polecenie</span><span class="sxs-lookup"><span data-stu-id="c336b-227">Command</span></span> | <span data-ttu-id="c336b-228">Funkcja</span><span class="sxs-lookup"><span data-stu-id="c336b-228">Function</span></span>
--- | ---
[<span data-ttu-id="c336b-229">dotnet add package</span><span class="sxs-lookup"><span data-stu-id="c336b-229">dotnet add package</span></span>](dotnet-add-package.md) | <span data-ttu-id="c336b-230">Dodaje pakiet NuGet.</span><span class="sxs-lookup"><span data-stu-id="c336b-230">Adds a NuGet package.</span></span>
[<span data-ttu-id="c336b-231">dotnet remove package</span><span class="sxs-lookup"><span data-stu-id="c336b-231">dotnet remove package</span></span>](dotnet-remove-package.md) | <span data-ttu-id="c336b-232">Usuwa pakiet NuGet.</span><span class="sxs-lookup"><span data-stu-id="c336b-232">Removes a NuGet package.</span></span>

### <a name="nuget-commands"></a><span data-ttu-id="c336b-233">Polecenia NuGet</span><span class="sxs-lookup"><span data-stu-id="c336b-233">NuGet commands</span></span>

<span data-ttu-id="c336b-234">Polecenie</span><span class="sxs-lookup"><span data-stu-id="c336b-234">Command</span></span> | <span data-ttu-id="c336b-235">Funkcja</span><span class="sxs-lookup"><span data-stu-id="c336b-235">Function</span></span>
--- | ---
[<span data-ttu-id="c336b-236">dotnet nuget delete</span><span class="sxs-lookup"><span data-stu-id="c336b-236">dotnet nuget delete</span></span>](dotnet-nuget-delete.md) | <span data-ttu-id="c336b-237">Usuwa lub usuwa listę pakiet z serwera.</span><span class="sxs-lookup"><span data-stu-id="c336b-237">Deletes or unlists a package from the server.</span></span>
[<span data-ttu-id="c336b-238">dotnet nuget push</span><span class="sxs-lookup"><span data-stu-id="c336b-238">dotnet nuget push</span></span>](dotnet-nuget-push.md) | <span data-ttu-id="c336b-239">Wypycha pakiet do serwera i publikuje go.</span><span class="sxs-lookup"><span data-stu-id="c336b-239">Pushes a package to the server and publishes it.</span></span>
[<span data-ttu-id="c336b-240">dotnet nuget locals</span><span class="sxs-lookup"><span data-stu-id="c336b-240">dotnet nuget locals</span></span>](dotnet-nuget-locals.md) | <span data-ttu-id="c336b-241">Czyści lub wyświetla lokalne zasoby NuGet, takie jak pamięć podręczna żądań http, tymczasowa pamięć podręczna lub folder pakietów globalnych dla całej maszyny.</span><span class="sxs-lookup"><span data-stu-id="c336b-241">Clears or lists local NuGet resources such as http-request cache, temporary cache, or machine-wide global packages folder.</span></span>
[<span data-ttu-id="c336b-242">dotnet nuget dodać źródło</span><span class="sxs-lookup"><span data-stu-id="c336b-242">dotnet nuget add source</span></span>](dotnet-nuget-add-source.md) | <span data-ttu-id="c336b-243">Dodaje źródło NuGet.</span><span class="sxs-lookup"><span data-stu-id="c336b-243">Adds a NuGet source.</span></span>
[<span data-ttu-id="c336b-244">dotnet nuget wyłącz źródło</span><span class="sxs-lookup"><span data-stu-id="c336b-244">dotnet nuget disable source</span></span>](dotnet-nuget-disable-source.md) | <span data-ttu-id="c336b-245">Wyłącza źródło NuGet.</span><span class="sxs-lookup"><span data-stu-id="c336b-245">Disables a NuGet source.</span></span>
[<span data-ttu-id="c336b-246">dotnet nuget włączyć źródło</span><span class="sxs-lookup"><span data-stu-id="c336b-246">dotnet nuget enable source</span></span>](dotnet-nuget-enable-source.md) | <span data-ttu-id="c336b-247">Włącza źródło NuGet.</span><span class="sxs-lookup"><span data-stu-id="c336b-247">Enables a NuGet source.</span></span>
[<span data-ttu-id="c336b-248">źródło listy dotnet nuget</span><span class="sxs-lookup"><span data-stu-id="c336b-248">dotnet nuget list source</span></span>](dotnet-nuget-list-source.md) | <span data-ttu-id="c336b-249">Wyświetla listę wszystkich skonfigurowanych źródeł NuGet.</span><span class="sxs-lookup"><span data-stu-id="c336b-249">Lists all configured NuGet sources.</span></span>
[<span data-ttu-id="c336b-250">dotnet nuget usunąć źródło</span><span class="sxs-lookup"><span data-stu-id="c336b-250">dotnet nuget remove source</span></span>](dotnet-nuget-remove-source.md) | <span data-ttu-id="c336b-251">Usuwa źródło NuGet.</span><span class="sxs-lookup"><span data-stu-id="c336b-251">Removes a NuGet source.</span></span>
[<span data-ttu-id="c336b-252">źródło aktualizacji dotnet nuget</span><span class="sxs-lookup"><span data-stu-id="c336b-252">dotnet nuget update source</span></span>](dotnet-nuget-update-source.md) | <span data-ttu-id="c336b-253">Aktualizuje źródło NuGet.</span><span class="sxs-lookup"><span data-stu-id="c336b-253">Updates a NuGet source.</span></span>

### <a name="global-tool-path-and-local-tools-commands"></a><span data-ttu-id="c336b-254">Polecenia narzędzi globalnych, ścieżki narzędzi i narzędzi lokalnych</span><span class="sxs-lookup"><span data-stu-id="c336b-254">Global, tool-path, and local tools commands</span></span>

<span data-ttu-id="c336b-255">Narzędzia są aplikacje konsoli, które są instalowane z pakietów NuGet i są wywoływane z wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="c336b-255">Tools are console applications that are installed from NuGet packages and are invoked from the command prompt.</span></span> <span data-ttu-id="c336b-256">Możesz samodzielnie napisać narzędzia lub zainstalować narzędzia napisane przez osoby trzecie.</span><span class="sxs-lookup"><span data-stu-id="c336b-256">You can write tools yourself or install tools written by third parties.</span></span> <span data-ttu-id="c336b-257">Narzędzia są również nazywane narzędziami globalnymi, narzędziami ścieżki narzędzi i narzędziami lokalnymi.</span><span class="sxs-lookup"><span data-stu-id="c336b-257">Tools are also known as global tools, tool-path tools, and local tools.</span></span> <span data-ttu-id="c336b-258">Aby uzyskać więcej informacji, zobacz [omówienie narzędzi .NET Core](global-tools.md).</span><span class="sxs-lookup"><span data-stu-id="c336b-258">For more information, see [.NET Core tools overview](global-tools.md).</span></span> <span data-ttu-id="c336b-259">Globalne i narzędzia ścieżki narzędzi są dostępne począwszy od .NET Core SDK 2.1.</span><span class="sxs-lookup"><span data-stu-id="c336b-259">Global and tool-path tools are available starting with .NET Core SDK 2.1.</span></span> <span data-ttu-id="c336b-260">Narzędzia lokalne są dostępne począwszy od .NET Core SDK 3.0.</span><span class="sxs-lookup"><span data-stu-id="c336b-260">Local tools are available starting with .NET Core SDK 3.0.</span></span>

<span data-ttu-id="c336b-261">Polecenie</span><span class="sxs-lookup"><span data-stu-id="c336b-261">Command</span></span> | <span data-ttu-id="c336b-262">Funkcja</span><span class="sxs-lookup"><span data-stu-id="c336b-262">Function</span></span>
--- | ---
[<span data-ttu-id="c336b-263">dotnet tool install</span><span class="sxs-lookup"><span data-stu-id="c336b-263">dotnet tool install</span></span>](dotnet-tool-install.md) | <span data-ttu-id="c336b-264">Instaluje narzędzie na komputerze.</span><span class="sxs-lookup"><span data-stu-id="c336b-264">Installs a tool on your machine.</span></span>
[<span data-ttu-id="c336b-265">dotnet tool list</span><span class="sxs-lookup"><span data-stu-id="c336b-265">dotnet tool list</span></span>](dotnet-tool-list.md) | <span data-ttu-id="c336b-266">Wyświetla listę wszystkich narzędzi globalnych, ścieżki narzędzi lub narzędzi lokalnych aktualnie zainstalowanych na komputerze.</span><span class="sxs-lookup"><span data-stu-id="c336b-266">Lists all global, tool-path, or local tools currently installed on your machine.</span></span>
[<span data-ttu-id="c336b-267">dotnet tool uninstall</span><span class="sxs-lookup"><span data-stu-id="c336b-267">dotnet tool uninstall</span></span>](dotnet-tool-uninstall.md) | <span data-ttu-id="c336b-268">Odinstalowuje narzędzie z komputera.</span><span class="sxs-lookup"><span data-stu-id="c336b-268">Uninstalls a tool from your machine.</span></span>
[<span data-ttu-id="c336b-269">dotnet tool update</span><span class="sxs-lookup"><span data-stu-id="c336b-269">dotnet tool update</span></span>](dotnet-tool-update.md) | <span data-ttu-id="c336b-270">Aktualizuje narzędzie zainstalowane na komputerze.</span><span class="sxs-lookup"><span data-stu-id="c336b-270">Updates a tool that is installed on your machine.</span></span>

### <a name="additional-tools"></a><span data-ttu-id="c336b-271">Dodatkowe narzędzia</span><span class="sxs-lookup"><span data-stu-id="c336b-271">Additional tools</span></span>

<span data-ttu-id="c336b-272">Począwszy od zestawu .NET Core SDK 2.1.300, wiele narzędzi, `DotnetCliToolReference` które były dostępne tylko na podstawie projektu, są teraz dostępne jako część zestawu .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="c336b-272">Starting with .NET Core SDK 2.1.300, a number of tools that were available only on a per project basis using `DotnetCliToolReference` are now available as part of the .NET Core SDK.</span></span> <span data-ttu-id="c336b-273">Narzędzia te są wymienione w poniższej tabeli:</span><span class="sxs-lookup"><span data-stu-id="c336b-273">These tools are listed in the following table:</span></span>

| <span data-ttu-id="c336b-274">Narzędzie</span><span class="sxs-lookup"><span data-stu-id="c336b-274">Tool</span></span>                                              | <span data-ttu-id="c336b-275">Funkcja</span><span class="sxs-lookup"><span data-stu-id="c336b-275">Function</span></span>                                                     |
| ------------------------------------------------- | ------------------------------------------------------------ |
| <span data-ttu-id="c336b-276">dev-certs</span><span class="sxs-lookup"><span data-stu-id="c336b-276">dev-certs</span></span>                                         | <span data-ttu-id="c336b-277">Tworzy certyfikaty deweloperów i zarządza nimi.</span><span class="sxs-lookup"><span data-stu-id="c336b-277">Creates and manages development certificates.</span></span>                |
| [<span data-ttu-id="c336b-278">Ef</span><span class="sxs-lookup"><span data-stu-id="c336b-278">ef</span></span>](/ef/core/miscellaneous/cli/dotnet)           | <span data-ttu-id="c336b-279">Narzędzia wiersza polecenia Core entity framework.</span><span class="sxs-lookup"><span data-stu-id="c336b-279">Entity Framework Core command-line tools.</span></span>                    |
| <span data-ttu-id="c336b-280">sql-cache</span><span class="sxs-lookup"><span data-stu-id="c336b-280">sql-cache</span></span>                                         | <span data-ttu-id="c336b-281">Narzędzia wiersza polecenia pamięci podręcznej programu SQL Server.</span><span class="sxs-lookup"><span data-stu-id="c336b-281">SQL Server cache command-line tools.</span></span>                         |
| [<span data-ttu-id="c336b-282">tajemnice użytkownika</span><span class="sxs-lookup"><span data-stu-id="c336b-282">user-secrets</span></span>](/aspnet/core/security/app-secrets) | <span data-ttu-id="c336b-283">Zarządza wpisami tajnymi użytkowników deweloperów.</span><span class="sxs-lookup"><span data-stu-id="c336b-283">Manages development user secrets.</span></span>                            |
| [<span data-ttu-id="c336b-284">Oglądać</span><span class="sxs-lookup"><span data-stu-id="c336b-284">watch</span></span>](/aspnet/core/tutorials/dotnet-watch)      | <span data-ttu-id="c336b-285">Uruchamia obserwatora plików, który uruchamia polecenie po zmianie plików.</span><span class="sxs-lookup"><span data-stu-id="c336b-285">Starts a file watcher that runs a command when files change.</span></span> |

<span data-ttu-id="c336b-286">Aby uzyskać więcej informacji `dotnet <tool-name> --help`o każdym narzędziu, wpisz .</span><span class="sxs-lookup"><span data-stu-id="c336b-286">For more information about each tool, type `dotnet <tool-name> --help`.</span></span>

## <a name="examples"></a><span data-ttu-id="c336b-287">Przykłady</span><span class="sxs-lookup"><span data-stu-id="c336b-287">Examples</span></span>

<span data-ttu-id="c336b-288">Utwórz nową aplikację konsoli .NET Core:</span><span class="sxs-lookup"><span data-stu-id="c336b-288">Create a new .NET Core console application:</span></span>

```dotnetcli
dotnet new console
```

<span data-ttu-id="c336b-289">Tworzenie projektu i jego zależności w danym katalogu:</span><span class="sxs-lookup"><span data-stu-id="c336b-289">Build a project and its dependencies in a given directory:</span></span>

```dotnetcli
dotnet build
```

<span data-ttu-id="c336b-290">Uruchamianie aplikacji:</span><span class="sxs-lookup"><span data-stu-id="c336b-290">Run an application:</span></span>

```dotnetcli
dotnet myapp.dll
```

## <a name="environment-variables"></a><span data-ttu-id="c336b-291">Zmienne środowiskowe</span><span class="sxs-lookup"><span data-stu-id="c336b-291">Environment variables</span></span>

- <span data-ttu-id="c336b-292">`DOTNET_ROOT`, `DOTNET_ROOT(x86)`</span><span class="sxs-lookup"><span data-stu-id="c336b-292">`DOTNET_ROOT`, `DOTNET_ROOT(x86)`</span></span>

  <span data-ttu-id="c336b-293">Określa lokalizację środowiska uruchomień .NET Core, jeśli nie są zainstalowane w lokalizacji domyślnej.</span><span class="sxs-lookup"><span data-stu-id="c336b-293">Specifies the location of the .NET Core runtimes, if they are not installed in the default location.</span></span> <span data-ttu-id="c336b-294">Domyślną lokalizacją `C:\Program Files\dotnet`w systemie Windows jest .</span><span class="sxs-lookup"><span data-stu-id="c336b-294">The default location on Windows is `C:\Program Files\dotnet`.</span></span> <span data-ttu-id="c336b-295">Domyślną lokalizacją w systemach Linux i macOS jest `/usr/share/dotnet`.</span><span class="sxs-lookup"><span data-stu-id="c336b-295">The default location on Linux and macOS is `/usr/share/dotnet`.</span></span> <span data-ttu-id="c336b-296">Ta zmienna środowiskowa jest używana tylko podczas uruchamiania aplikacji za pośrednictwem wygenerowanych plików wykonywalnych (apphosts).</span><span class="sxs-lookup"><span data-stu-id="c336b-296">This environment variable is used only when running apps via generated executables (apphosts).</span></span> <span data-ttu-id="c336b-297">`DOTNET_ROOT(x86)`jest używany podczas uruchamiania 32-bitowego pliku wykonywalnego na 64-bitowym os.</span><span class="sxs-lookup"><span data-stu-id="c336b-297">`DOTNET_ROOT(x86)` is used instead when running a 32-bit executable on a 64-bit OS.</span></span>

- `DOTNET_PACKAGES`

  <span data-ttu-id="c336b-298">Folder pakietów globalnych.</span><span class="sxs-lookup"><span data-stu-id="c336b-298">The global packages folder.</span></span> <span data-ttu-id="c336b-299">Jeśli nie jest ustawiona, domyślnie jest to `~/.nuget/packages` w systemie Unix lub `%userprofile%\.nuget\packages` Windows.</span><span class="sxs-lookup"><span data-stu-id="c336b-299">If not set, it defaults to `~/.nuget/packages` on Unix or `%userprofile%\.nuget\packages` on Windows.</span></span>

- `DOTNET_SERVICING`

  <span data-ttu-id="c336b-300">Określa lokalizację indeksu obsługi do użycia przez hosta udostępnionego podczas ładowania środowiska wykonawczego.</span><span class="sxs-lookup"><span data-stu-id="c336b-300">Specifies the location of the servicing index to use by the shared host when loading the runtime.</span></span>

- `DOTNET_NOLOGO`

  <span data-ttu-id="c336b-301">Określa, czy komunikaty powitalne .NET Core i telemetryczne są wyświetlane przy pierwszym uruchomieniu.</span><span class="sxs-lookup"><span data-stu-id="c336b-301">Specifies whether .NET Core welcome and telemetry messages are displayed on first run.</span></span> <span data-ttu-id="c336b-302">Ustaw, `true` aby wyciszyć `true`te `1`komunikaty `yes` (wartości , `false` lub zaakceptowane) lub ustawić, aby zezwolić (wartości `false`, `0`, lub `no` akceptowane).</span><span class="sxs-lookup"><span data-stu-id="c336b-302">Set to `true` to mute these messages (values `true`, `1`, or `yes` accepted) or set to `false` to allow (values `false`, `0`, or `no` accepted).</span></span> <span data-ttu-id="c336b-303">Jeśli nie jest ustawiona, domyślna jest `false` i komunikaty będą wyświetlane przy pierwszym uruchomieniu.</span><span class="sxs-lookup"><span data-stu-id="c336b-303">If not set, the default is `false` and the messages will be displayed on first run.</span></span> <span data-ttu-id="c336b-304">Należy zauważyć, że ta flaga `DOTNET_CLI_TELEMETRY_OPTOUT` nie ma wpływu na dane telemetryczne (zobacz rezygnacji z wysyłania danych telemetrycznych).</span><span class="sxs-lookup"><span data-stu-id="c336b-304">Note that this flag has no effect on telemetry (see `DOTNET_CLI_TELEMETRY_OPTOUT` for opting out of sending telemetry).</span></span>

- `DOTNET_CLI_TELEMETRY_OPTOUT`

  <span data-ttu-id="c336b-305">Określa, czy dane dotyczące użycia narzędzi .NET Core są zbierane i wysyłane do firmy Microsoft.</span><span class="sxs-lookup"><span data-stu-id="c336b-305">Specifies whether data about the .NET Core tools usage is collected and sent to Microsoft.</span></span> <span data-ttu-id="c336b-306">Ustaw `true` opcję rezygnacji z funkcji telemetrii (wartości `true`lub `1` `yes` zaakceptowane).</span><span class="sxs-lookup"><span data-stu-id="c336b-306">Set to `true` to opt-out of the telemetry feature (values `true`, `1`, or `yes` accepted).</span></span> <span data-ttu-id="c336b-307">W przeciwnym `false` razie należy ustawić opcję wyboru `false` `0`funkcji `no` telemetrycznych (wartości lub zaakceptowanych).</span><span class="sxs-lookup"><span data-stu-id="c336b-307">Otherwise, set to `false` to opt into the telemetry features (values `false`, `0`, or `no` accepted).</span></span> <span data-ttu-id="c336b-308">Jeśli nie jest ustawiona, ustawieniem domyślnym jest `false` funkcja telemetrii.</span><span class="sxs-lookup"><span data-stu-id="c336b-308">If not set, the default is `false` and the telemetry feature is active.</span></span>

- `DOTNET_MULTILEVEL_LOOKUP`

  <span data-ttu-id="c336b-309">Określa, czy środowisko uruchomieniowe .NET Core, współużytkowana struktura lub SDK są rozpoznawane z lokalizacji globalnej.</span><span class="sxs-lookup"><span data-stu-id="c336b-309">Specifies whether .NET Core runtime, shared framework, or SDK are resolved from the global location.</span></span> <span data-ttu-id="c336b-310">Jeśli nie jest ustawiona, domyślnie `true`jest to 1 (logiczne ).</span><span class="sxs-lookup"><span data-stu-id="c336b-310">If not set, it defaults to 1 (logical `true`).</span></span> <span data-ttu-id="c336b-311">Ustaw wartość 0 `false`(logiczna), aby nie rozwiązać problemu z lokalizacji globalnej i mieć izolowane instalacje .NET Core.</span><span class="sxs-lookup"><span data-stu-id="c336b-311">Set to 0 (logical `false`) to not resolve from the global location and have isolated .NET Core installations.</span></span> <span data-ttu-id="c336b-312">Aby uzyskać więcej informacji na temat wyszukiwania wielopoziomowego, zobacz [Wielopoziomowe wyszukiwanie SharedFX](https://github.com/dotnet/core-setup/blob/master/Documentation/design-docs/multilevel-sharedfx-lookup.md).</span><span class="sxs-lookup"><span data-stu-id="c336b-312">For more information about multi-level lookup, see [Multi-level SharedFX Lookup](https://github.com/dotnet/core-setup/blob/master/Documentation/design-docs/multilevel-sharedfx-lookup.md).</span></span>

- <span data-ttu-id="c336b-313">`DOTNET_ROLL_FORWARD`**Dostępne począwszy od .NET Core 3.x SDK.**</span><span class="sxs-lookup"><span data-stu-id="c336b-313">`DOTNET_ROLL_FORWARD` **Available starting with .NET Core 3.x SDK.**</span></span>

  <span data-ttu-id="c336b-314">Określa zachowanie przewijania do przodu.</span><span class="sxs-lookup"><span data-stu-id="c336b-314">Determines roll forward behavior.</span></span> <span data-ttu-id="c336b-315">Aby uzyskać więcej `--roll-forward` informacji, zobacz opcję wcześniej w tym artykule.</span><span class="sxs-lookup"><span data-stu-id="c336b-315">For more information, see the `--roll-forward` option earlier in this article.</span></span>

- <span data-ttu-id="c336b-316">`DOTNET_ROLL_FORWARD_ON_NO_CANDIDATE_FX`**Dostępne w pliku .NET Core 2.x SDK.**</span><span class="sxs-lookup"><span data-stu-id="c336b-316">`DOTNET_ROLL_FORWARD_ON_NO_CANDIDATE_FX` **Available in .NET Core 2.x SDK.**</span></span>

  <span data-ttu-id="c336b-317">Wyłącza wersję pomocniczą do `0`przodu, jeśli jest ustawiona na .</span><span class="sxs-lookup"><span data-stu-id="c336b-317">Disables minor version roll forward, if set to `0`.</span></span> <span data-ttu-id="c336b-318">Aby uzyskać więcej informacji, zobacz [Przewij do przodu](../whats-new/dotnet-core-2-1.md#roll-forward).</span><span class="sxs-lookup"><span data-stu-id="c336b-318">For more information, see [Roll forward](../whats-new/dotnet-core-2-1.md#roll-forward).</span></span>

- `DOTNET_CLI_UI_LANGUAGE`

  <span data-ttu-id="c336b-319">Ustawia język interfejsu użytkownika interfejsu wiersza polecenia `en-us`przy użyciu wartości ustawień regionalnych, takich jak .</span><span class="sxs-lookup"><span data-stu-id="c336b-319">Sets the language of the CLI UI using a locale value such as `en-us`.</span></span> <span data-ttu-id="c336b-320">Obsługiwane wartości są takie same jak w programie Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="c336b-320">The supported values are the same as for Visual Studio.</span></span> <span data-ttu-id="c336b-321">Aby uzyskać więcej informacji, zobacz sekcję dotyczącą zmieniania języka instalatora w [dokumentacji instalacji programu Visual Studio](https://docs.microsoft.com/visualstudio/install/install-visual-studio?view=vs-2019).</span><span class="sxs-lookup"><span data-stu-id="c336b-321">For more information, see the section on changing the installer language in the [Visual Studio installation documentation](https://docs.microsoft.com/visualstudio/install/install-visual-studio?view=vs-2019).</span></span> <span data-ttu-id="c336b-322">Zasady Menedżera zasobów .NET mają zastosowanie, więc nie trzeba&mdash;wybierać dopasowania dokładnego, które można również wybrać elementy podrzędne w `CultureInfo` drzewie.</span><span class="sxs-lookup"><span data-stu-id="c336b-322">The .NET resource manager rules apply, so you don't have to pick an exact match&mdash;you can also pick descendants in the `CultureInfo` tree.</span></span> <span data-ttu-id="c336b-323">Na przykład, jeśli ustawisz go na `fr-CA`, `fr` CLI znajdzie i użyje tłumaczeń.</span><span class="sxs-lookup"><span data-stu-id="c336b-323">For example, if you set it to `fr-CA`, the CLI will find and use the `fr` translations.</span></span> <span data-ttu-id="c336b-324">Jeśli ustawisz go na język, który nie jest obsługiwany, cli powróci do języka angielskiego.</span><span class="sxs-lookup"><span data-stu-id="c336b-324">If you set it to a language that is not supported, the CLI falls back to English.</span></span>

- `DOTNET_DISABLE_GUI_ERRORS`

  <span data-ttu-id="c336b-325">W przypadku generowanych plików wykonywalnych z funkcją GUI — wyłącza okno dialogowe, które zwykle jest wyświetlane dla niektórych klas błędów.</span><span class="sxs-lookup"><span data-stu-id="c336b-325">For GUI-enabled generated executables - disables dialog popup, which normally shows for certain classes of errors.</span></span> <span data-ttu-id="c336b-326">To tylko zapisuje `stderr` i kończy się w tych przypadkach.</span><span class="sxs-lookup"><span data-stu-id="c336b-326">It only writes to `stderr` and exits in those cases.</span></span>
  
- `DOTNET_ADDITIONAL_DEPS`

  <span data-ttu-id="c336b-327">Odpowiednik opcji `--additional-deps`interfejsu wiersza polecenia .</span><span class="sxs-lookup"><span data-stu-id="c336b-327">Equivalent to CLI option `--additional-deps`.</span></span>

- `DOTNET_RUNTIME_ID`

  <span data-ttu-id="c336b-328">Zastępuje wykryty identyfikator RID.</span><span class="sxs-lookup"><span data-stu-id="c336b-328">Overrides the detected RID.</span></span>

- `DOTNET_SHARED_STORE`

  <span data-ttu-id="c336b-329">Lokalizacja "magazynu udostępnionego", do którego rozdzielczość zestawu powraca w niektórych przypadkach.</span><span class="sxs-lookup"><span data-stu-id="c336b-329">Location of the "shared store" which assembly resolution falls back to in some cases.</span></span>

- `DOTNET_STARTUP_HOOKS`

  <span data-ttu-id="c336b-330">Lista zestawów do załadowania i wykonania haków startowych.</span><span class="sxs-lookup"><span data-stu-id="c336b-330">List of assemblies to load and execute startup hooks from.</span></span>

- <span data-ttu-id="c336b-331">`COREHOST_TRACE`, `COREHOST_TRACEFILE`, `COREHOST_TRACE_VERBOSITY`</span><span class="sxs-lookup"><span data-stu-id="c336b-331">`COREHOST_TRACE`, `COREHOST_TRACEFILE`, `COREHOST_TRACE_VERBOSITY`</span></span>

  <span data-ttu-id="c336b-332">Steruje śledzeniem diagnostyki ze składników `dotnet.exe` `hostfxr`hostingu, takich jak , i `hostpolicy`.</span><span class="sxs-lookup"><span data-stu-id="c336b-332">Controls diagnostics tracing from the hosting components, such as `dotnet.exe`, `hostfxr`, and `hostpolicy`.</span></span>

## <a name="see-also"></a><span data-ttu-id="c336b-333">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c336b-333">See also</span></span>

- [<span data-ttu-id="c336b-334">Pliki konfiguracji środowiska wykonawczego</span><span class="sxs-lookup"><span data-stu-id="c336b-334">Runtime Configuration Files</span></span>](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md)
- [<span data-ttu-id="c336b-335">Ustawienia konfiguracji w czasie wykonywania rdzenia .NET</span><span class="sxs-lookup"><span data-stu-id="c336b-335">.NET Core run-time configuration settings</span></span>](../run-time-config/index.md)
