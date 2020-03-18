---
title: polecenie dotnet
description: Dowiedz się więcej o komendzie dotnet (sterownik ogólny dla wiersza wiersza polecenia .NET Core) i jego użyciu.
ms.date: 02/13/2020
ms.openlocfilehash: da37c5cc3b019851e245fa3f65ae9dfb8a3fef54
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79398896"
---
# <a name="dotnet-command"></a><span data-ttu-id="0317e-103">polecenie dotnet</span><span class="sxs-lookup"><span data-stu-id="0317e-103">dotnet command</span></span>

<span data-ttu-id="0317e-104">**Ten artykuł dotyczy:** ✔️ .NET Core 2.1 SDK i nowszych wersji</span><span class="sxs-lookup"><span data-stu-id="0317e-104">**This article applies to:** ✔️ .NET Core 2.1 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="0317e-105">Nazwa</span><span class="sxs-lookup"><span data-stu-id="0317e-105">Name</span></span>

<span data-ttu-id="0317e-106">`dotnet`- Ogólny sterownik dla .NET Core CLI.</span><span class="sxs-lookup"><span data-stu-id="0317e-106">`dotnet` - The generic driver for the .NET Core CLI.</span></span>

## <a name="synopsis"></a><span data-ttu-id="0317e-107">Streszczenie</span><span class="sxs-lookup"><span data-stu-id="0317e-107">Synopsis</span></span>

<span data-ttu-id="0317e-108">Aby uzyskać informacje o dostępnych poleceniach i środowisku:</span><span class="sxs-lookup"><span data-stu-id="0317e-108">To get information about the available commands and the environment:</span></span>

```dotnetcli
dotnet [-h|--help] [--version] [--info]
    [--list-runtimes] [--list-sdks]
```

<span data-ttu-id="0317e-109">Aby uruchomić polecenie (wymaga instalacji zestawu SDK):</span><span class="sxs-lookup"><span data-stu-id="0317e-109">To run a command (requires SDK installation):</span></span>

```dotnetcli
dotnet <COMMAND> [-d|--diagnostics] [-h|--help] [--verbosity]
    [command-options] [arguments]
```

<span data-ttu-id="0317e-110">Aby uruchomić aplikację:</span><span class="sxs-lookup"><span data-stu-id="0317e-110">To run an application:</span></span>

```dotnetcli
dotnet [--additionalprobingpath] [--additional-deps]
    [--fx-version]  [--roll-forward]
    <PATH_TO_APPLICATION> [arguments]

dotnet exec [--additionalprobingpath] [--additional-deps]
    [--fx-version]  [--roll-forward]
    <PATH_TO_APPLICATION> [arguments]
```

<span data-ttu-id="0317e-111">`--roll-forward`jest dostępna od .NET Core 3.x.</span><span class="sxs-lookup"><span data-stu-id="0317e-111">`--roll-forward` is available since .NET Core 3.x.</span></span> <span data-ttu-id="0317e-112">Użyj `--roll-forward-on-no-candidate-fx` dla .NET Core 2.x.</span><span class="sxs-lookup"><span data-stu-id="0317e-112">Use `--roll-forward-on-no-candidate-fx` for .NET Core 2.x.</span></span>

## <a name="description"></a><span data-ttu-id="0317e-113">Opis</span><span class="sxs-lookup"><span data-stu-id="0317e-113">Description</span></span>

<span data-ttu-id="0317e-114">Polecenie `dotnet` ma dwie funkcje:</span><span class="sxs-lookup"><span data-stu-id="0317e-114">The `dotnet` command has two functions:</span></span>

- <span data-ttu-id="0317e-115">Zawiera polecenia do pracy z projektami .NET Core.</span><span class="sxs-lookup"><span data-stu-id="0317e-115">It provides commands for working with .NET Core projects.</span></span>

  <span data-ttu-id="0317e-116">Na przykład [`dotnet build`](dotnet-build.md) tworzy projekt.</span><span class="sxs-lookup"><span data-stu-id="0317e-116">For example, [`dotnet build`](dotnet-build.md) builds a project.</span></span> <span data-ttu-id="0317e-117">Każde polecenie definiuje własne opcje i argumenty.</span><span class="sxs-lookup"><span data-stu-id="0317e-117">Each command defines its own options and arguments.</span></span> <span data-ttu-id="0317e-118">Wszystkie polecenia obsługują `--help` opcję drukowania krótkiej dokumentacji dotyczącej używania polecenia.</span><span class="sxs-lookup"><span data-stu-id="0317e-118">All commands support the `--help` option for printing out brief documentation about how to use the command.</span></span>

- <span data-ttu-id="0317e-119">Uruchamia aplikacje .NET Core.</span><span class="sxs-lookup"><span data-stu-id="0317e-119">It runs .NET Core applications.</span></span>

  <span data-ttu-id="0317e-120">Należy określić ścieżkę `.dll` do pliku aplikacji, aby uruchomić aplikację.</span><span class="sxs-lookup"><span data-stu-id="0317e-120">You specify the path to an application `.dll` file to run the application.</span></span> <span data-ttu-id="0317e-121">Na przykład `dotnet myapp.dll` uruchamia `myapp` aplikację.</span><span class="sxs-lookup"><span data-stu-id="0317e-121">For example, `dotnet myapp.dll` runs the `myapp` application.</span></span> <span data-ttu-id="0317e-122">Zobacz [.NET Core wdrożenia aplikacji,](../deploying/index.md) aby dowiedzieć się więcej o opcjach wdrażania.</span><span class="sxs-lookup"><span data-stu-id="0317e-122">See [.NET Core application deployment](../deploying/index.md) to learn about deployment options.</span></span>

## <a name="options"></a><span data-ttu-id="0317e-123">Opcje</span><span class="sxs-lookup"><span data-stu-id="0317e-123">Options</span></span>

<span data-ttu-id="0317e-124">Różne opcje są `dotnet` dostępne dla siebie, do uruchamiania polecenia i uruchamiania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="0317e-124">Different options are available for `dotnet` by itself, for running a command, and for running an application.</span></span>

### <a name="options-for-dotnet-by-itself"></a><span data-ttu-id="0317e-125">Opcje dotnet usiebie</span><span class="sxs-lookup"><span data-stu-id="0317e-125">Options for dotnet by itself</span></span>

<span data-ttu-id="0317e-126">Następujące opcje są `dotnet` same w sobie.</span><span class="sxs-lookup"><span data-stu-id="0317e-126">The following options are for `dotnet` by itself.</span></span> <span data-ttu-id="0317e-127">Na przykład `dotnet --info`.</span><span class="sxs-lookup"><span data-stu-id="0317e-127">For example, `dotnet --info`.</span></span> <span data-ttu-id="0317e-128">Drukują informacje o środowisku.</span><span class="sxs-lookup"><span data-stu-id="0317e-128">They print out information about the environment.</span></span>

- **`--info`**

  <span data-ttu-id="0317e-129">Drukuje szczegółowe informacje o instalacji .NET Core i środowisku komputera, takie jak bieżący system operacyjny, i zatwierdza sha wersji .NET Core.</span><span class="sxs-lookup"><span data-stu-id="0317e-129">Prints out detailed information about a .NET Core installation and the machine environment, such as the current operating system, and commit SHA of the .NET Core version.</span></span>

- **`--version`**

  <span data-ttu-id="0317e-130">Drukuje używana wersja programu .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="0317e-130">Prints out the version of the .NET Core SDK in use.</span></span>

- **`--list-runtimes`**

  <span data-ttu-id="0317e-131">Drukuje listę zainstalowanych uruchomień programu .NET Core.</span><span class="sxs-lookup"><span data-stu-id="0317e-131">Prints out a list of the installed .NET Core runtimes.</span></span>

- **`--list-sdks`**

  <span data-ttu-id="0317e-132">Drukuje listę zainstalowanych zestawów SDK .NET Core.</span><span class="sxs-lookup"><span data-stu-id="0317e-132">Prints out a list of the installed .NET Core SDKs.</span></span>

- **`-h|--help`**

  <span data-ttu-id="0317e-133">Drukuje listę dostępnych poleceń.</span><span class="sxs-lookup"><span data-stu-id="0317e-133">Prints out a list of available commands.</span></span>

### <a name="sdk-options-for-running-a-command"></a><span data-ttu-id="0317e-134">Opcje sdk uruchamiania polecenia</span><span class="sxs-lookup"><span data-stu-id="0317e-134">SDK options for running a command</span></span>

<span data-ttu-id="0317e-135">Następujące opcje są `dotnet` dla z poleceniem.</span><span class="sxs-lookup"><span data-stu-id="0317e-135">The following options are for `dotnet` with a command.</span></span> <span data-ttu-id="0317e-136">Na przykład `dotnet build --help`.</span><span class="sxs-lookup"><span data-stu-id="0317e-136">For example, `dotnet build --help`.</span></span>

- **`-d|--diagnostics`**

  <span data-ttu-id="0317e-137">Umożliwia wyjście diagnostyczne.</span><span class="sxs-lookup"><span data-stu-id="0317e-137">Enables diagnostic output.</span></span>

- **`-v|--verbosity <LEVEL>`**

  <span data-ttu-id="0317e-138">Ustawia poziom szczegółowości polecenia.</span><span class="sxs-lookup"><span data-stu-id="0317e-138">Sets the verbosity level of the command.</span></span> <span data-ttu-id="0317e-139">Dozwolone wartości `q[uiet]` `m[inimal]`to `n[ormal]` `d[etailed]`, `diag[nostic]`, , i .</span><span class="sxs-lookup"><span data-stu-id="0317e-139">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="0317e-140">Nie jest obsługiwany w każdym poleceniu.</span><span class="sxs-lookup"><span data-stu-id="0317e-140">Not supported in every command.</span></span> <span data-ttu-id="0317e-141">Zobacz określoną stronę polecenia, aby ustalić, czy ta opcja jest dostępna.</span><span class="sxs-lookup"><span data-stu-id="0317e-141">See specific command page to determine if this option is available.</span></span>

- **`-h|--help`**

  <span data-ttu-id="0317e-142">Drukuje dokumentację dla danego polecenia, na przykład `dotnet build --help`.</span><span class="sxs-lookup"><span data-stu-id="0317e-142">Prints out documentation for a given command, such as `dotnet build --help`.</span></span>

- **`command options`**

  <span data-ttu-id="0317e-143">Każde polecenie definiuje opcje specyficzne dla tego polecenia.</span><span class="sxs-lookup"><span data-stu-id="0317e-143">Each command defines options specific to that command.</span></span> <span data-ttu-id="0317e-144">Zobacz konkretną stronę polecenia, aby uzyskać listę dostępnych opcji.</span><span class="sxs-lookup"><span data-stu-id="0317e-144">See specific command page for a list of available options.</span></span>

### <a name="runtime-options"></a><span data-ttu-id="0317e-145">Opcje czasu wykonywania</span><span class="sxs-lookup"><span data-stu-id="0317e-145">Runtime options</span></span>

<span data-ttu-id="0317e-146">Następujące opcje są `dotnet` dostępne po uruchomieniu aplikacji.</span><span class="sxs-lookup"><span data-stu-id="0317e-146">The following options are available when `dotnet` runs an application.</span></span> <span data-ttu-id="0317e-147">Na przykład `dotnet myapp.dll --fx-version 3.1.1`.</span><span class="sxs-lookup"><span data-stu-id="0317e-147">For example, `dotnet myapp.dll --fx-version 3.1.1`.</span></span>

- **`--additionalprobingpath <PATH>`**

  <span data-ttu-id="0317e-148">Ścieżka zawierająca zasady sondowania i zestawy do sondowania.</span><span class="sxs-lookup"><span data-stu-id="0317e-148">Path containing probing policy and assemblies to probe.</span></span>

- **`--additional-deps <PATH>`**

  <span data-ttu-id="0317e-149">Ścieżka do dodatkowego pliku *.deps.json.*</span><span class="sxs-lookup"><span data-stu-id="0317e-149">Path to an additional *.deps.json* file.</span></span> <span data-ttu-id="0317e-150">Plik *deps.json* zawiera listę zależności, zależności kompilacji i informacje o wersji używane do rozwiązywania konfliktów zestawów.</span><span class="sxs-lookup"><span data-stu-id="0317e-150">A *deps.json* file contains a list of dependencies, compilation dependencies, and version information used to address assembly conflicts.</span></span> <span data-ttu-id="0317e-151">Aby uzyskać więcej informacji, zobacz [Pliki konfiguracyjne w czasie wykonywania](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md) w usteercie GitHub.</span><span class="sxs-lookup"><span data-stu-id="0317e-151">For more information, see [Runtime Configuration Files](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md) on GitHub.</span></span>

- **`--fx-version <VERSION>`**

  <span data-ttu-id="0317e-152">Wersja programu runtime .NET Core do użycia do uruchamiania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="0317e-152">Version of the .NET Core runtime to use to run the application.</span></span>

- **`--runtimeconfig`**

  <span data-ttu-id="0317e-153">Ścieżka do pliku *runtimeconfig.json.*</span><span class="sxs-lookup"><span data-stu-id="0317e-153">Path to a *runtimeconfig.json* file.</span></span> <span data-ttu-id="0317e-154">Plik *runtimeconfig.json* to plik konfiguracyjny zawierający ustawienia czasu wykonywania.</span><span class="sxs-lookup"><span data-stu-id="0317e-154">A *runtimeconfig.json* file is a configuration file that contains run-time settings.</span></span> <span data-ttu-id="0317e-155">Aby uzyskać więcej informacji, zobacz [ustawienia konfiguracji środowiska uruchomieniowego .NET Core](../run-time-config/index.md#runtimeconfigjson).</span><span class="sxs-lookup"><span data-stu-id="0317e-155">For more information, see [.NET Core run-time configuration settings](../run-time-config/index.md#runtimeconfigjson).</span></span>

- <span data-ttu-id="0317e-156">**`--roll-forward-on-no-candidate-fx <N>`\*\*\*\*Dostępne w sdk .NET Core 2.x.**</span><span class="sxs-lookup"><span data-stu-id="0317e-156">**`--roll-forward-on-no-candidate-fx <N>`** **Available in .NET Core 2.x SDK.**</span></span>

  <span data-ttu-id="0317e-157">Definiuje zachowanie, gdy wymagana struktura współużytkowana nie jest dostępna.</span><span class="sxs-lookup"><span data-stu-id="0317e-157">Defines behavior when the required shared framework is not available.</span></span> <span data-ttu-id="0317e-158">`N`może być:</span><span class="sxs-lookup"><span data-stu-id="0317e-158">`N` can be:</span></span>

  - <span data-ttu-id="0317e-159">`0`- Wyłącz nawet drobne wersji roll do przodu.</span><span class="sxs-lookup"><span data-stu-id="0317e-159">`0` - Disable even minor version roll forward.</span></span>
  - <span data-ttu-id="0317e-160">`1`- Przewiń do przodu na wersji pomocniczej, ale nie w wersji głównej.</span><span class="sxs-lookup"><span data-stu-id="0317e-160">`1` - Roll forward on minor version, but not on major version.</span></span> <span data-ttu-id="0317e-161">Jest to zachowanie domyślne.</span><span class="sxs-lookup"><span data-stu-id="0317e-161">This is the default behavior.</span></span>
  - <span data-ttu-id="0317e-162">`2`- Przewiń do przodu na mniejszych i głównych wersjach.</span><span class="sxs-lookup"><span data-stu-id="0317e-162">`2` - Roll forward on minor and major versions.</span></span>

   <span data-ttu-id="0317e-163">Aby uzyskać więcej informacji, zobacz [Przewijanie do przodu](../whats-new/dotnet-core-2-1.md#roll-forward).</span><span class="sxs-lookup"><span data-stu-id="0317e-163">For more information, see [Roll forward](../whats-new/dotnet-core-2-1.md#roll-forward).</span></span>

- <span data-ttu-id="0317e-164">**`--roll-forward <SETTING>`\*\*\*\*Dostępne od .NET Core SDK 3.0.**</span><span class="sxs-lookup"><span data-stu-id="0317e-164">**`--roll-forward <SETTING>`** **Available starting with .NET Core SDK 3.0.**</span></span>

  <span data-ttu-id="0317e-165">Określa sposób stosowania rolowania do przodu aplikacji.</span><span class="sxs-lookup"><span data-stu-id="0317e-165">Controls how roll forward is applied to the app.</span></span> <span data-ttu-id="0317e-166">Może `SETTING` być jedną z następujących wartości.</span><span class="sxs-lookup"><span data-stu-id="0317e-166">The `SETTING` can be one of the following values.</span></span> <span data-ttu-id="0317e-167">Jeśli nie zostanie `Minor` określony, jest ustawieniem domyślnym.</span><span class="sxs-lookup"><span data-stu-id="0317e-167">If not specified, `Minor` is the default.</span></span>

  - <span data-ttu-id="0317e-168">`LatestPatch`- Przewiń do przodu do najwyższej wersji poprawki.</span><span class="sxs-lookup"><span data-stu-id="0317e-168">`LatestPatch` - Roll forward to the highest patch version.</span></span> <span data-ttu-id="0317e-169">Spowoduje to wyłączenie pomocniczej wersji przewijania do przodu.</span><span class="sxs-lookup"><span data-stu-id="0317e-169">This disables minor version roll forward.</span></span>
  - <span data-ttu-id="0317e-170">`Minor`- Przewiń do przodu do najniższej wyższej wersji pomocniczej, jeśli brakuje żądanej wersji pomocniczej.</span><span class="sxs-lookup"><span data-stu-id="0317e-170">`Minor` - Roll forward to the lowest higher minor version, if requested minor version is missing.</span></span> <span data-ttu-id="0317e-171">Jeśli występuje żądana wersja pomocnicza, używana jest zasada LatestPatch.</span><span class="sxs-lookup"><span data-stu-id="0317e-171">If the requested minor version is present, then the LatestPatch policy is used.</span></span>
  - <span data-ttu-id="0317e-172">`Major`- Przewiń do przodu do najniższej wyższej wersji głównej i najniższej wersji pomocniczej, jeśli nie ma żądanej wersji głównej.</span><span class="sxs-lookup"><span data-stu-id="0317e-172">`Major` - Roll forward to lowest higher major version, and lowest minor version, if requested major version is missing.</span></span> <span data-ttu-id="0317e-173">Jeśli występuje żądana wersja główna, używana jest zasada pomocnicza.</span><span class="sxs-lookup"><span data-stu-id="0317e-173">If the requested major version is present, then the Minor policy is used.</span></span>
  - <span data-ttu-id="0317e-174">`LatestMinor`- Przewiń do najwyższej wersji pomocniczej, nawet jeśli wymagana wersja pomocnicza jest obecna.</span><span class="sxs-lookup"><span data-stu-id="0317e-174">`LatestMinor` - Roll forward to highest minor version, even if requested minor version is present.</span></span> <span data-ttu-id="0317e-175">Przeznaczone dla scenariuszy hostingu składników.</span><span class="sxs-lookup"><span data-stu-id="0317e-175">Intended for component hosting scenarios.</span></span>
  - <span data-ttu-id="0317e-176">`LatestMajor`- Przewiń do najwyższej wersji głównej i najwyższej wersji pomocniczej, nawet jeśli wymagane jest poważne.</span><span class="sxs-lookup"><span data-stu-id="0317e-176">`LatestMajor` - Roll forward to highest major and highest minor version, even if requested major is present.</span></span> <span data-ttu-id="0317e-177">Przeznaczone dla scenariuszy hostingu składników.</span><span class="sxs-lookup"><span data-stu-id="0317e-177">Intended for component hosting scenarios.</span></span>
  - <span data-ttu-id="0317e-178">`Disable`- Nie przewracaj się do przodu.</span><span class="sxs-lookup"><span data-stu-id="0317e-178">`Disable` - Don't roll forward.</span></span> <span data-ttu-id="0317e-179">Powiąż tylko określoną wersję.</span><span class="sxs-lookup"><span data-stu-id="0317e-179">Only bind to specified version.</span></span> <span data-ttu-id="0317e-180">Ta zasada nie jest zalecane do ogólnego użytku, ponieważ wyłącza możliwość przewijania do przodu do najnowszych poprawek.</span><span class="sxs-lookup"><span data-stu-id="0317e-180">This policy isn't recommended for general use because it disables the ability to roll forward to the latest patches.</span></span> <span data-ttu-id="0317e-181">Ta wartość jest zalecana tylko do testowania.</span><span class="sxs-lookup"><span data-stu-id="0317e-181">This value is only recommended for testing.</span></span>

<span data-ttu-id="0317e-182">Z wyjątkiem `Disable`, wszystkie ustawienia będą korzystać z najwyższej dostępnej wersji poprawki.</span><span class="sxs-lookup"><span data-stu-id="0317e-182">With the exception of `Disable`, all settings will use the highest available patch version.</span></span>

<span data-ttu-id="0317e-183">Zachowanie do przodu można również skonfigurować we właściwości pliku projektu, właściwości pliku konfiguracyjnego w czasie wykonywania i zmiennej środowiskowej.</span><span class="sxs-lookup"><span data-stu-id="0317e-183">Roll forward behavior can also be configured in a project file property, a run-time configuration file property, and an environment variable.</span></span> <span data-ttu-id="0317e-184">Aby uzyskać więcej informacji, zobacz [Główne wersje uruchomieniowej do przodu](../whats-new/dotnet-core-3-0.md#major-version-runtime-roll-forward).</span><span class="sxs-lookup"><span data-stu-id="0317e-184">For more information, see [Major-version runtime roll forward](../whats-new/dotnet-core-3-0.md#major-version-runtime-roll-forward).</span></span>

## <a name="dotnet-commands"></a><span data-ttu-id="0317e-185">Polecenia dotnet</span><span class="sxs-lookup"><span data-stu-id="0317e-185">dotnet commands</span></span>

### <a name="general"></a><span data-ttu-id="0317e-186">Ogólne</span><span class="sxs-lookup"><span data-stu-id="0317e-186">General</span></span>

| <span data-ttu-id="0317e-187">Polecenie</span><span class="sxs-lookup"><span data-stu-id="0317e-187">Command</span></span>                                       | <span data-ttu-id="0317e-188">Funkcja</span><span class="sxs-lookup"><span data-stu-id="0317e-188">Function</span></span>                                                            |
| --------------------------------------------- | ------------------------------------------------------------------- |
| [<span data-ttu-id="0317e-189">dotnet build</span><span class="sxs-lookup"><span data-stu-id="0317e-189">dotnet build</span></span>](dotnet-build.md)               | <span data-ttu-id="0317e-190">Tworzy aplikację .NET Core.</span><span class="sxs-lookup"><span data-stu-id="0317e-190">Builds a .NET Core application.</span></span>                                     |
| [<span data-ttu-id="0317e-191">dotnet build-server</span><span class="sxs-lookup"><span data-stu-id="0317e-191">dotnet build-server</span></span>](dotnet-build-server.md) | <span data-ttu-id="0317e-192">Współdziała z serwerami uruchomionymi przez kompilację.</span><span class="sxs-lookup"><span data-stu-id="0317e-192">Interacts with servers started by a build.</span></span>                          |
| [<span data-ttu-id="0317e-193">dotnet clean</span><span class="sxs-lookup"><span data-stu-id="0317e-193">dotnet clean</span></span>](dotnet-clean.md)               | <span data-ttu-id="0317e-194">Czyste wyjścia kompilacji.</span><span class="sxs-lookup"><span data-stu-id="0317e-194">Clean build outputs.</span></span>                                                |
| [<span data-ttu-id="0317e-195">dotnet help</span><span class="sxs-lookup"><span data-stu-id="0317e-195">dotnet help</span></span>](dotnet-help.md)                 | <span data-ttu-id="0317e-196">Pokazuje bardziej szczegółową dokumentację w trybie online dla polecenia.</span><span class="sxs-lookup"><span data-stu-id="0317e-196">Shows more detailed documentation online for the command.</span></span>           |
| [<span data-ttu-id="0317e-197">dotnet migrate</span><span class="sxs-lookup"><span data-stu-id="0317e-197">dotnet migrate</span></span>](dotnet-migrate.md)           | <span data-ttu-id="0317e-198">Migracja prawidłowego projektu podglądu 2 do projektu .NET Core SDK 1.0.</span><span class="sxs-lookup"><span data-stu-id="0317e-198">Migrates a valid Preview 2 project to a .NET Core SDK 1.0 project.</span></span>  |
| [<span data-ttu-id="0317e-199">dotnet msbuild</span><span class="sxs-lookup"><span data-stu-id="0317e-199">dotnet msbuild</span></span>](dotnet-msbuild.md)           | <span data-ttu-id="0317e-200">Zapewnia dostęp do wiersza polecenia MSBuild.</span><span class="sxs-lookup"><span data-stu-id="0317e-200">Provides access to the MSBuild command line.</span></span>                        |
| [<span data-ttu-id="0317e-201">dotnet new</span><span class="sxs-lookup"><span data-stu-id="0317e-201">dotnet new</span></span>](dotnet-new.md)                   | <span data-ttu-id="0317e-202">Inicjuje projekt języka C# lub F# dla danego szablonu.</span><span class="sxs-lookup"><span data-stu-id="0317e-202">Initializes a C# or F# project for a given template.</span></span>                |
| [<span data-ttu-id="0317e-203">dotnet pack</span><span class="sxs-lookup"><span data-stu-id="0317e-203">dotnet pack</span></span>](dotnet-pack.md)                 | <span data-ttu-id="0317e-204">Tworzy pakiet NuGet kodu.</span><span class="sxs-lookup"><span data-stu-id="0317e-204">Creates a NuGet package of your code.</span></span>                               |
| [<span data-ttu-id="0317e-205">dotnet publish</span><span class="sxs-lookup"><span data-stu-id="0317e-205">dotnet publish</span></span>](dotnet-publish.md)           | <span data-ttu-id="0317e-206">Publikuje aplikację zależną od platformy .NET lub niezależną.</span><span class="sxs-lookup"><span data-stu-id="0317e-206">Publishes a .NET framework-dependent or self-contained application.</span></span> |
| [<span data-ttu-id="0317e-207">dotnet restore</span><span class="sxs-lookup"><span data-stu-id="0317e-207">dotnet restore</span></span>](dotnet-restore.md)           | <span data-ttu-id="0317e-208">Przywraca zależności dla danej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="0317e-208">Restores the dependencies for a given application.</span></span>                  |
| [<span data-ttu-id="0317e-209">dotnet run</span><span class="sxs-lookup"><span data-stu-id="0317e-209">dotnet run</span></span>](dotnet-run.md)                   | <span data-ttu-id="0317e-210">Uruchamia aplikację ze źródła.</span><span class="sxs-lookup"><span data-stu-id="0317e-210">Runs the application from source.</span></span>                                   |
| [<span data-ttu-id="0317e-211">dotnet sln</span><span class="sxs-lookup"><span data-stu-id="0317e-211">dotnet sln</span></span>](dotnet-sln.md)                   | <span data-ttu-id="0317e-212">Opcje dodawania, usuwania i wystawiania projektów w pliku rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="0317e-212">Options to add, remove, and list projects in a solution file.</span></span>       |
| [<span data-ttu-id="0317e-213">dotnet store</span><span class="sxs-lookup"><span data-stu-id="0317e-213">dotnet store</span></span>](dotnet-store.md)               | <span data-ttu-id="0317e-214">Przechowuje zestawy w magazynie pakietów w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="0317e-214">Stores assemblies in the runtime package store.</span></span>                     |
| [<span data-ttu-id="0317e-215">dotnet test</span><span class="sxs-lookup"><span data-stu-id="0317e-215">dotnet test</span></span>](dotnet-test.md)                 | <span data-ttu-id="0317e-216">Uruchamia testy przy użyciu biegacza testowego.</span><span class="sxs-lookup"><span data-stu-id="0317e-216">Runs tests using a test runner.</span></span>                                     |

### <a name="project-references"></a><span data-ttu-id="0317e-217">Odwołania projektu</span><span class="sxs-lookup"><span data-stu-id="0317e-217">Project references</span></span>

<span data-ttu-id="0317e-218">Polecenie</span><span class="sxs-lookup"><span data-stu-id="0317e-218">Command</span></span> | <span data-ttu-id="0317e-219">Funkcja</span><span class="sxs-lookup"><span data-stu-id="0317e-219">Function</span></span>
--- | ---
[<span data-ttu-id="0317e-220">dotnet add reference</span><span class="sxs-lookup"><span data-stu-id="0317e-220">dotnet add reference</span></span>](dotnet-add-reference.md) | <span data-ttu-id="0317e-221">Dodaje odwołanie do projektu.</span><span class="sxs-lookup"><span data-stu-id="0317e-221">Adds a project reference.</span></span>
[<span data-ttu-id="0317e-222">dotnet list reference</span><span class="sxs-lookup"><span data-stu-id="0317e-222">dotnet list reference</span></span>](dotnet-list-reference.md) | <span data-ttu-id="0317e-223">Wyświetla listę odwołań do projektu.</span><span class="sxs-lookup"><span data-stu-id="0317e-223">Lists project references.</span></span>
[<span data-ttu-id="0317e-224">dotnet remove reference</span><span class="sxs-lookup"><span data-stu-id="0317e-224">dotnet remove reference</span></span>](dotnet-remove-reference.md) | <span data-ttu-id="0317e-225">Usuwa odwołanie do projektu.</span><span class="sxs-lookup"><span data-stu-id="0317e-225">Removes a project reference.</span></span>

### <a name="nuget-packages"></a><span data-ttu-id="0317e-226">Pakiety NuGet</span><span class="sxs-lookup"><span data-stu-id="0317e-226">NuGet packages</span></span>

<span data-ttu-id="0317e-227">Polecenie</span><span class="sxs-lookup"><span data-stu-id="0317e-227">Command</span></span> | <span data-ttu-id="0317e-228">Funkcja</span><span class="sxs-lookup"><span data-stu-id="0317e-228">Function</span></span>
--- | ---
[<span data-ttu-id="0317e-229">dotnet add package</span><span class="sxs-lookup"><span data-stu-id="0317e-229">dotnet add package</span></span>](dotnet-add-package.md) | <span data-ttu-id="0317e-230">Dodaje pakiet NuGet.</span><span class="sxs-lookup"><span data-stu-id="0317e-230">Adds a NuGet package.</span></span>
[<span data-ttu-id="0317e-231">dotnet remove package</span><span class="sxs-lookup"><span data-stu-id="0317e-231">dotnet remove package</span></span>](dotnet-remove-package.md) | <span data-ttu-id="0317e-232">Usuwa pakiet NuGet.</span><span class="sxs-lookup"><span data-stu-id="0317e-232">Removes a NuGet package.</span></span>

### <a name="nuget-commands"></a><span data-ttu-id="0317e-233">Polecenia NuGet</span><span class="sxs-lookup"><span data-stu-id="0317e-233">NuGet commands</span></span>

<span data-ttu-id="0317e-234">Polecenie</span><span class="sxs-lookup"><span data-stu-id="0317e-234">Command</span></span> | <span data-ttu-id="0317e-235">Funkcja</span><span class="sxs-lookup"><span data-stu-id="0317e-235">Function</span></span>
--- | ---
[<span data-ttu-id="0317e-236">dotnet nuget delete</span><span class="sxs-lookup"><span data-stu-id="0317e-236">dotnet nuget delete</span></span>](dotnet-nuget-delete.md) | <span data-ttu-id="0317e-237">Usuwa lub usuwa listę pakietu z serwera.</span><span class="sxs-lookup"><span data-stu-id="0317e-237">Deletes or unlists a package from the server.</span></span>
[<span data-ttu-id="0317e-238">dotnet nuget locals</span><span class="sxs-lookup"><span data-stu-id="0317e-238">dotnet nuget locals</span></span>](dotnet-nuget-locals.md) | <span data-ttu-id="0317e-239">Czyści lub wyświetla listę lokalnych zasobów NuGet, takich jak pamięć podręczna żądań http, tymczasowa pamięć podręczna lub folder pakietów globalnych dla całego komputera.</span><span class="sxs-lookup"><span data-stu-id="0317e-239">Clears or lists local NuGet resources such as http-request cache, temporary cache, or machine-wide global packages folder.</span></span>
[<span data-ttu-id="0317e-240">dotnet nuget push</span><span class="sxs-lookup"><span data-stu-id="0317e-240">dotnet nuget push</span></span>](dotnet-nuget-push.md) | <span data-ttu-id="0317e-241">Wypycha pakiet do serwera i publikuje go.</span><span class="sxs-lookup"><span data-stu-id="0317e-241">Pushes a package to the server and publishes it.</span></span>

### <a name="global-tool-path-and-local-tools-commands"></a><span data-ttu-id="0317e-242">Polecenia narzędzia globalnego, ścieżki narzędzia i narzędzia lokalne</span><span class="sxs-lookup"><span data-stu-id="0317e-242">Global, tool-path, and local tools commands</span></span>

<span data-ttu-id="0317e-243">Narzędzia są aplikacje konsoli, które są instalowane z pakietów NuGet i są wywoływane z wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="0317e-243">Tools are console applications that are installed from NuGet packages and are invoked from the command prompt.</span></span> <span data-ttu-id="0317e-244">Możesz samodzielnie pisać narzędzia lub instalować narzędzia napisane przez osoby trzecie.</span><span class="sxs-lookup"><span data-stu-id="0317e-244">You can write tools yourself or install tools written by third parties.</span></span> <span data-ttu-id="0317e-245">Narzędzia są również znane jako narzędzia globalne, narzędzia ścieżki narzędziowej i narzędzia lokalne.</span><span class="sxs-lookup"><span data-stu-id="0317e-245">Tools are also known as global tools, tool-path tools, and local tools.</span></span> <span data-ttu-id="0317e-246">Aby uzyskać więcej informacji, zobacz [omówienie narzędzi .NET Core](global-tools.md).</span><span class="sxs-lookup"><span data-stu-id="0317e-246">For more information, see [.NET Core tools overview](global-tools.md).</span></span> <span data-ttu-id="0317e-247">Globalne i narzędzia ścieżki są dostępne począwszy od .NET Core SDK 2.1.</span><span class="sxs-lookup"><span data-stu-id="0317e-247">Global and tool-path tools are available starting with .NET Core SDK 2.1.</span></span> <span data-ttu-id="0317e-248">Lokalne narzędzia są dostępne począwszy od .NET Core SDK 3.0.</span><span class="sxs-lookup"><span data-stu-id="0317e-248">Local tools are available starting with .NET Core SDK 3.0.</span></span>

<span data-ttu-id="0317e-249">Polecenie</span><span class="sxs-lookup"><span data-stu-id="0317e-249">Command</span></span> | <span data-ttu-id="0317e-250">Funkcja</span><span class="sxs-lookup"><span data-stu-id="0317e-250">Function</span></span>
--- | ---
[<span data-ttu-id="0317e-251">dotnet tool install</span><span class="sxs-lookup"><span data-stu-id="0317e-251">dotnet tool install</span></span>](dotnet-tool-install.md) | <span data-ttu-id="0317e-252">Instaluje narzędzie na komputerze.</span><span class="sxs-lookup"><span data-stu-id="0317e-252">Installs a tool on your machine.</span></span>
[<span data-ttu-id="0317e-253">dotnet tool list</span><span class="sxs-lookup"><span data-stu-id="0317e-253">dotnet tool list</span></span>](dotnet-tool-list.md) | <span data-ttu-id="0317e-254">Wyświetla listę wszystkich narzędzi globalnych, ścieżki narzędziowej lub lokalnych aktualnie zainstalowanych na komputerze.</span><span class="sxs-lookup"><span data-stu-id="0317e-254">Lists all global, tool-path, or local tools currently installed on your machine.</span></span>
[<span data-ttu-id="0317e-255">dotnet tool uninstall</span><span class="sxs-lookup"><span data-stu-id="0317e-255">dotnet tool uninstall</span></span>](dotnet-tool-uninstall.md) | <span data-ttu-id="0317e-256">Odinstalowuje narzędzie z komputera.</span><span class="sxs-lookup"><span data-stu-id="0317e-256">Uninstalls a tool from your machine.</span></span>
[<span data-ttu-id="0317e-257">dotnet tool update</span><span class="sxs-lookup"><span data-stu-id="0317e-257">dotnet tool update</span></span>](dotnet-tool-update.md) | <span data-ttu-id="0317e-258">Aktualizuje narzędzie zainstalowane na komputerze.</span><span class="sxs-lookup"><span data-stu-id="0317e-258">Updates a tool that is installed on your machine.</span></span>

### <a name="additional-tools"></a><span data-ttu-id="0317e-259">Dodatkowe narzędzia</span><span class="sxs-lookup"><span data-stu-id="0317e-259">Additional tools</span></span>

<span data-ttu-id="0317e-260">Począwszy od .NET Core SDK 2.1.300, liczba narzędzi, które `DotnetCliToolReference` były dostępne tylko na podstawie projektu przy użyciu są teraz dostępne jako część .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="0317e-260">Starting with .NET Core SDK 2.1.300, a number of tools that were available only on a per project basis using `DotnetCliToolReference` are now available as part of the .NET Core SDK.</span></span> <span data-ttu-id="0317e-261">Narzędzia te są wymienione w poniższej tabeli:</span><span class="sxs-lookup"><span data-stu-id="0317e-261">These tools are listed in the following table:</span></span>

| <span data-ttu-id="0317e-262">Narzędzie</span><span class="sxs-lookup"><span data-stu-id="0317e-262">Tool</span></span>                                              | <span data-ttu-id="0317e-263">Funkcja</span><span class="sxs-lookup"><span data-stu-id="0317e-263">Function</span></span>                                                     |
| ------------------------------------------------- | ------------------------------------------------------------ |
| <span data-ttu-id="0317e-264">dev-certs</span><span class="sxs-lookup"><span data-stu-id="0317e-264">dev-certs</span></span>                                         | <span data-ttu-id="0317e-265">Tworzy certyfikaty deweloperów i zarządza nimi.</span><span class="sxs-lookup"><span data-stu-id="0317e-265">Creates and manages development certificates.</span></span>                |
| [<span data-ttu-id="0317e-266">Ef</span><span class="sxs-lookup"><span data-stu-id="0317e-266">ef</span></span>](/ef/core/miscellaneous/cli/dotnet)           | <span data-ttu-id="0317e-267">Narzędzia wiersza polecenia Entity Framework Core.</span><span class="sxs-lookup"><span data-stu-id="0317e-267">Entity Framework Core command-line tools.</span></span>                    |
| <span data-ttu-id="0317e-268">sql-cache</span><span class="sxs-lookup"><span data-stu-id="0317e-268">sql-cache</span></span>                                         | <span data-ttu-id="0317e-269">Narzędzia wiersza polecenia pamięci podręcznej programu SQL Server.</span><span class="sxs-lookup"><span data-stu-id="0317e-269">SQL Server cache command-line tools.</span></span>                         |
| [<span data-ttu-id="0317e-270">tajemnice użytkownika</span><span class="sxs-lookup"><span data-stu-id="0317e-270">user-secrets</span></span>](/aspnet/core/security/app-secrets) | <span data-ttu-id="0317e-271">Zarządza wtajemnicami użytkowników deweloperskich.</span><span class="sxs-lookup"><span data-stu-id="0317e-271">Manages development user secrets.</span></span>                            |
| [<span data-ttu-id="0317e-272">Oglądać</span><span class="sxs-lookup"><span data-stu-id="0317e-272">watch</span></span>](/aspnet/core/tutorials/dotnet-watch)      | <span data-ttu-id="0317e-273">Uruchamia obserwatora plików, który uruchamia polecenie po zmianie plików.</span><span class="sxs-lookup"><span data-stu-id="0317e-273">Starts a file watcher that runs a command when files change.</span></span> |

<span data-ttu-id="0317e-274">Aby uzyskać więcej informacji `dotnet <tool-name> --help`na temat każdego narzędzia, wpisz .</span><span class="sxs-lookup"><span data-stu-id="0317e-274">For more information about each tool, type `dotnet <tool-name> --help`.</span></span>

## <a name="examples"></a><span data-ttu-id="0317e-275">Przykłady</span><span class="sxs-lookup"><span data-stu-id="0317e-275">Examples</span></span>

<span data-ttu-id="0317e-276">Utwórz nową aplikację konsoli .NET Core:</span><span class="sxs-lookup"><span data-stu-id="0317e-276">Create a new .NET Core console application:</span></span>

```dotnetcli
dotnet new console
```

<span data-ttu-id="0317e-277">Tworzenie projektu i jego zależności w danym katalogu:</span><span class="sxs-lookup"><span data-stu-id="0317e-277">Build a project and its dependencies in a given directory:</span></span>

```dotnetcli
dotnet build
```

<span data-ttu-id="0317e-278">Uruchom aplikację:</span><span class="sxs-lookup"><span data-stu-id="0317e-278">Run an application:</span></span>

```dotnetcli
dotnet myapp.dll
```

## <a name="environment-variables"></a><span data-ttu-id="0317e-279">Zmienne środowiskowe</span><span class="sxs-lookup"><span data-stu-id="0317e-279">Environment variables</span></span>

- <span data-ttu-id="0317e-280">`DOTNET_ROOT`, `DOTNET_ROOT(x86)`</span><span class="sxs-lookup"><span data-stu-id="0317e-280">`DOTNET_ROOT`, `DOTNET_ROOT(x86)`</span></span>

  <span data-ttu-id="0317e-281">Określa lokalizację runii programu .NET Core, jeśli nie są one zainstalowane w lokalizacji domyślnej.</span><span class="sxs-lookup"><span data-stu-id="0317e-281">Specifies the location of the .NET Core runtimes, if they are not installed in the default location.</span></span> <span data-ttu-id="0317e-282">Domyślną lokalizacją `C:\Program Files\dotnet`w systemie Windows jest .</span><span class="sxs-lookup"><span data-stu-id="0317e-282">The default location on Windows is `C:\Program Files\dotnet`.</span></span> <span data-ttu-id="0317e-283">Domyślną lokalizacją w systemach `/usr/share/dotnet`Linux i macOS jest .</span><span class="sxs-lookup"><span data-stu-id="0317e-283">The default location on Linux and macOS is `/usr/share/dotnet`.</span></span> <span data-ttu-id="0317e-284">Ta zmienna środowiskowa jest używana tylko podczas uruchamiania aplikacji za pośrednictwem wygenerowanych plików wykonywalnych (hostów aplikacji).</span><span class="sxs-lookup"><span data-stu-id="0317e-284">This environment variable is used only when running apps via generated executables (apphosts).</span></span> <span data-ttu-id="0317e-285">`DOTNET_ROOT(x86)`jest używany zamiast tego podczas uruchamiania 32-bitowego pliku wykonywalnego w 64-bitowym os.</span><span class="sxs-lookup"><span data-stu-id="0317e-285">`DOTNET_ROOT(x86)` is used instead when running a 32-bit executable on a 64-bit OS.</span></span>

- `DOTNET_PACKAGES`

  <span data-ttu-id="0317e-286">Folder pakietów globalnych.</span><span class="sxs-lookup"><span data-stu-id="0317e-286">The global packages folder.</span></span> <span data-ttu-id="0317e-287">Jeśli nie jest ustawiona, `~/.nuget/packages` domyślnie `%userprofile%\.nuget\packages` w systemie Unix lub w systemie Windows.</span><span class="sxs-lookup"><span data-stu-id="0317e-287">If not set, it defaults to `~/.nuget/packages` on Unix or `%userprofile%\.nuget\packages` on Windows.</span></span>

- `DOTNET_SERVICING`

  <span data-ttu-id="0317e-288">Określa lokalizację indeksu obsługi, który ma być używany przez hosta udostępnionego podczas ładowania czasu wykonywania.</span><span class="sxs-lookup"><span data-stu-id="0317e-288">Specifies the location of the servicing index to use by the shared host when loading the runtime.</span></span>

- `DOTNET_CLI_TELEMETRY_OPTOUT`

  <span data-ttu-id="0317e-289">Określa, czy dane dotyczące użycia narzędzi programu .NET Core są zbierane i wysyłane do firmy Microsoft.</span><span class="sxs-lookup"><span data-stu-id="0317e-289">Specifies whether data about the .NET Core tools usage is collected and sent to Microsoft.</span></span> <span data-ttu-id="0317e-290">Ustaw, `true` aby zrezygnować z funkcji telemetrii (wartości `true`, `1`lub `yes` zaakceptowane).</span><span class="sxs-lookup"><span data-stu-id="0317e-290">Set to `true` to opt-out of the telemetry feature (values `true`, `1`, or `yes` accepted).</span></span> <span data-ttu-id="0317e-291">W przeciwnym `false` razie ustaw, aby zdecydować `false` `0`się `no` na funkcje telemetrii (wartości , lub zaakceptowane).</span><span class="sxs-lookup"><span data-stu-id="0317e-291">Otherwise, set to `false` to opt into the telemetry features (values `false`, `0`, or `no` accepted).</span></span> <span data-ttu-id="0317e-292">Jeśli nie jest ustawiona, domyślnie jest `false` i funkcja telemetrii jest aktywny.</span><span class="sxs-lookup"><span data-stu-id="0317e-292">If not set, the default is `false` and the telemetry feature is active.</span></span>

- `DOTNET_MULTILEVEL_LOOKUP`

  <span data-ttu-id="0317e-293">Określa, czy program .NET Core, framework udostępniony lub SDK są rozpoznawani z lokalizacji globalnej.</span><span class="sxs-lookup"><span data-stu-id="0317e-293">Specifies whether .NET Core runtime, shared framework, or SDK are resolved from the global location.</span></span> <span data-ttu-id="0317e-294">Jeśli nie jest ustawiona, domyślnie `true`jest ustawiona na 1 (logiczna ).</span><span class="sxs-lookup"><span data-stu-id="0317e-294">If not set, it defaults to 1 (logical `true`).</span></span> <span data-ttu-id="0317e-295">Ustaw wartość 0 `false`(logiczną), aby nie rozpoznawać z lokalizacji globalnej i mieć izolowane instalacje .NET Core.</span><span class="sxs-lookup"><span data-stu-id="0317e-295">Set to 0 (logical `false`) to not resolve from the global location and have isolated .NET Core installations.</span></span> <span data-ttu-id="0317e-296">Aby uzyskać więcej informacji na temat wyszukiwania wielopoziomowego, zobacz [Wielopoziomowe wyszukiwania SharedFX](https://github.com/dotnet/core-setup/blob/master/Documentation/design-docs/multilevel-sharedfx-lookup.md).</span><span class="sxs-lookup"><span data-stu-id="0317e-296">For more information about multi-level lookup, see [Multi-level SharedFX Lookup](https://github.com/dotnet/core-setup/blob/master/Documentation/design-docs/multilevel-sharedfx-lookup.md).</span></span>

- <span data-ttu-id="0317e-297">`DOTNET_ROLL_FORWARD`**Dostępne od .NET Core 3.x SDK.**</span><span class="sxs-lookup"><span data-stu-id="0317e-297">`DOTNET_ROLL_FORWARD` **Available starting with .NET Core 3.x SDK.**</span></span>

  <span data-ttu-id="0317e-298">Określa zachowanie rzutdo przodu.</span><span class="sxs-lookup"><span data-stu-id="0317e-298">Determines roll forward behavior.</span></span> <span data-ttu-id="0317e-299">Aby uzyskać więcej `--roll-forward` informacji, zobacz opcję wcześniej w tym artykule.</span><span class="sxs-lookup"><span data-stu-id="0317e-299">For more information, see the `--roll-forward` option earlier in this article.</span></span>

- <span data-ttu-id="0317e-300">`DOTNET_ROLL_FORWARD_ON_NO_CANDIDATE_FX`**Dostępne w sdk .NET Core 2.x.**</span><span class="sxs-lookup"><span data-stu-id="0317e-300">`DOTNET_ROLL_FORWARD_ON_NO_CANDIDATE_FX` **Available in .NET Core 2.x SDK.**</span></span>

  <span data-ttu-id="0317e-301">Wyłącza pomocnicze juz rolki `0`wersji do przodu, jeśli jest ustawiona na .</span><span class="sxs-lookup"><span data-stu-id="0317e-301">Disables minor version roll forward, if set to `0`.</span></span> <span data-ttu-id="0317e-302">Aby uzyskać więcej informacji, zobacz [Przewijanie do przodu](../whats-new/dotnet-core-2-1.md#roll-forward).</span><span class="sxs-lookup"><span data-stu-id="0317e-302">For more information, see [Roll forward](../whats-new/dotnet-core-2-1.md#roll-forward).</span></span>

- `DOTNET_CLI_UI_LANGUAGE`

  <span data-ttu-id="0317e-303">Sets the language of the CLI UI using a locale value such as `en-us`.</span><span class="sxs-lookup"><span data-stu-id="0317e-303">Sets the language of the CLI UI using a locale value such as `en-us`.</span></span> <span data-ttu-id="0317e-304">Obsługiwane wartości są takie same jak w programie Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="0317e-304">The supported values are the same as for Visual Studio.</span></span> <span data-ttu-id="0317e-305">Aby uzyskać więcej informacji, zobacz sekcję dotyczącą zmiany języka instalatora w [dokumentacji instalacyjnej programu Visual Studio](https://docs.microsoft.com/visualstudio/install/install-visual-studio?view=vs-2019).</span><span class="sxs-lookup"><span data-stu-id="0317e-305">For more information, see the section on changing the installer language in the [Visual Studio installation documentation](https://docs.microsoft.com/visualstudio/install/install-visual-studio?view=vs-2019).</span></span> <span data-ttu-id="0317e-306">Reguły Menedżera zasobów .NET mają zastosowanie, więc nie trzeba&mdash;wybrać dokładne dopasowanie można `CultureInfo` również wybrać elementy podrzędne w drzewie.</span><span class="sxs-lookup"><span data-stu-id="0317e-306">The .NET resource manager rules apply, so you don't have to pick an exact match&mdash;you can also pick descendants in the `CultureInfo` tree.</span></span> <span data-ttu-id="0317e-307">Na przykład, jeśli ustawisz go na `fr-CA`, `fr` CLI znajdzie i użyje tłumaczenia.</span><span class="sxs-lookup"><span data-stu-id="0317e-307">For example, if you set it to `fr-CA`, the CLI will find and use the `fr` translations.</span></span> <span data-ttu-id="0317e-308">Jeśli ustawisz go na język, który nie jest obsługiwany, cli wraca do języka angielskiego.</span><span class="sxs-lookup"><span data-stu-id="0317e-308">If you set it to a language that is not supported, the CLI falls back to English.</span></span>

- `DOTNET_DISABLE_GUI_ERRORS`

  <span data-ttu-id="0317e-309">Dla pliku plików wykonywalnych generowanych przez gui - wyłącza okno podręczne okna dialogowego, które zwykle pokazuje dla niektórych klas błędów.</span><span class="sxs-lookup"><span data-stu-id="0317e-309">For GUI-enabled generated executables - disables dialog popup which normally shows for certain classes of errors.</span></span> <span data-ttu-id="0317e-310">W takich przypadkach `stderr` pisze tylko do i wychodzi.</span><span class="sxs-lookup"><span data-stu-id="0317e-310">It only writes to `stderr` and exits in those cases.</span></span>
  
- `DOTNET_ADDITIONAL_DEPS`

  <span data-ttu-id="0317e-311">Odpowiednik opcji `--additional-deps`CLI .</span><span class="sxs-lookup"><span data-stu-id="0317e-311">Equivalent to CLI option `--additional-deps`.</span></span>

- `DOTNET_RUNTIME_ID`

  <span data-ttu-id="0317e-312">Zastępuje wykryty identyfikator RID.</span><span class="sxs-lookup"><span data-stu-id="0317e-312">Overrides the detected RID.</span></span>

- `DOTNET_SHARED_STORE`

  <span data-ttu-id="0317e-313">Lokalizacja "magazynu udostępnionego", do którego w niektórych przypadkach powraca rozdzielczość zestawu.</span><span class="sxs-lookup"><span data-stu-id="0317e-313">Location of the "shared store" which assembly resolution falls back to in some cases.</span></span>

- `DOTNET_STARTUP_HOOKS`

  <span data-ttu-id="0317e-314">Lista zestawów do ładowania i wykonywania haków startowych z.</span><span class="sxs-lookup"><span data-stu-id="0317e-314">List of assemblies to load and execute startup hooks from.</span></span>

- <span data-ttu-id="0317e-315">`COREHOST_TRACE`, `COREHOST_TRACEFILE`, `COREHOST_TRACE_VERBOSITY`</span><span class="sxs-lookup"><span data-stu-id="0317e-315">`COREHOST_TRACE`, `COREHOST_TRACEFILE`, `COREHOST_TRACE_VERBOSITY`</span></span>

  <span data-ttu-id="0317e-316">Steruje śledzeniem diagnostycznym ze `dotnet.exe`składników `hostfxr`hostingu, takich jak , , i `hostpolicy`.</span><span class="sxs-lookup"><span data-stu-id="0317e-316">Controls diagnostics tracing from the hosting components, such as `dotnet.exe`, `hostfxr`, and `hostpolicy`.</span></span>

## <a name="see-also"></a><span data-ttu-id="0317e-317">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="0317e-317">See also</span></span>

- [<span data-ttu-id="0317e-318">Pliki konfiguracyjne czasu wykonywania</span><span class="sxs-lookup"><span data-stu-id="0317e-318">Runtime Configuration Files</span></span>](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md)
- [<span data-ttu-id="0317e-319">Ustawienia konfiguracji środowiska .NET Core w czasie wykonywania</span><span class="sxs-lookup"><span data-stu-id="0317e-319">.NET Core run-time configuration settings</span></span>](../run-time-config/index.md)
