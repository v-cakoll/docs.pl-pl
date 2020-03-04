---
title: dotnet — polecenie
description: Dowiedz się więcej na temat polecenia dotnet (sterownika generycznego dla interfejs wiersza polecenia platformy .NET Core) i jego użycia.
ms.date: 02/13/2020
ms.openlocfilehash: da37c5cc3b019851e245fa3f65ae9dfb8a3fef54
ms.sourcegitcommit: 43d10ef65f0f1fd6c3b515e363bde11a3fcd8d6d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/03/2020
ms.locfileid: "78240873"
---
# <a name="dotnet-command"></a><span data-ttu-id="ebd8a-103">dotnet — polecenie</span><span class="sxs-lookup"><span data-stu-id="ebd8a-103">dotnet command</span></span>

<span data-ttu-id="ebd8a-104">**Ten artykuł ma zastosowanie do:** ✔️ .net Core 2,1 SDK i nowszych wersjach</span><span class="sxs-lookup"><span data-stu-id="ebd8a-104">**This article applies to:** ✔️ .NET Core 2.1 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="ebd8a-105">Name (Nazwa)</span><span class="sxs-lookup"><span data-stu-id="ebd8a-105">Name</span></span>

<span data-ttu-id="ebd8a-106">`dotnet` — sterownik ogólny interfejs wiersza polecenia platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="ebd8a-106">`dotnet` - The generic driver for the .NET Core CLI.</span></span>

## <a name="synopsis"></a><span data-ttu-id="ebd8a-107">Streszczenie</span><span class="sxs-lookup"><span data-stu-id="ebd8a-107">Synopsis</span></span>

<span data-ttu-id="ebd8a-108">Aby uzyskać informacje na temat dostępnych poleceń i środowiska:</span><span class="sxs-lookup"><span data-stu-id="ebd8a-108">To get information about the available commands and the environment:</span></span>

```dotnetcli
dotnet [-h|--help] [--version] [--info]
    [--list-runtimes] [--list-sdks]
```

<span data-ttu-id="ebd8a-109">Aby uruchomić polecenie (wymaga instalacji zestawu SDK):</span><span class="sxs-lookup"><span data-stu-id="ebd8a-109">To run a command (requires SDK installation):</span></span>

```dotnetcli
dotnet <COMMAND> [-d|--diagnostics] [-h|--help] [--verbosity]
    [command-options] [arguments]
```

<span data-ttu-id="ebd8a-110">Aby uruchomić aplikację:</span><span class="sxs-lookup"><span data-stu-id="ebd8a-110">To run an application:</span></span>

```dotnetcli
dotnet [--additionalprobingpath] [--additional-deps]
    [--fx-version]  [--roll-forward]
    <PATH_TO_APPLICATION> [arguments]

dotnet exec [--additionalprobingpath] [--additional-deps]
    [--fx-version]  [--roll-forward]
    <PATH_TO_APPLICATION> [arguments]
```

<span data-ttu-id="ebd8a-111">`--roll-forward` jest dostępna od platformy .NET Core 3. x.</span><span class="sxs-lookup"><span data-stu-id="ebd8a-111">`--roll-forward` is available since .NET Core 3.x.</span></span> <span data-ttu-id="ebd8a-112">Użyj `--roll-forward-on-no-candidate-fx` dla platformy .NET Core 2. x.</span><span class="sxs-lookup"><span data-stu-id="ebd8a-112">Use `--roll-forward-on-no-candidate-fx` for .NET Core 2.x.</span></span>

## <a name="description"></a><span data-ttu-id="ebd8a-113">Opis</span><span class="sxs-lookup"><span data-stu-id="ebd8a-113">Description</span></span>

<span data-ttu-id="ebd8a-114">Polecenie `dotnet` ma dwie funkcje:</span><span class="sxs-lookup"><span data-stu-id="ebd8a-114">The `dotnet` command has two functions:</span></span>

- <span data-ttu-id="ebd8a-115">Zawiera polecenia umożliwiające pracę z projektami .NET Core.</span><span class="sxs-lookup"><span data-stu-id="ebd8a-115">It provides commands for working with .NET Core projects.</span></span>

  <span data-ttu-id="ebd8a-116">Na przykład [`dotnet build`](dotnet-build.md) kompiluje projekt.</span><span class="sxs-lookup"><span data-stu-id="ebd8a-116">For example, [`dotnet build`](dotnet-build.md) builds a project.</span></span> <span data-ttu-id="ebd8a-117">Każde polecenie definiuje własne opcje i argumenty.</span><span class="sxs-lookup"><span data-stu-id="ebd8a-117">Each command defines its own options and arguments.</span></span> <span data-ttu-id="ebd8a-118">Wszystkie polecenia obsługują opcję `--help` do drukowania krótkiej dokumentacji dotyczącej sposobu korzystania z polecenia.</span><span class="sxs-lookup"><span data-stu-id="ebd8a-118">All commands support the `--help` option for printing out brief documentation about how to use the command.</span></span>

- <span data-ttu-id="ebd8a-119">Uruchamia aplikacje platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="ebd8a-119">It runs .NET Core applications.</span></span>

  <span data-ttu-id="ebd8a-120">Należy określić ścieżkę do pliku `.dll` aplikacji, aby uruchomić aplikację.</span><span class="sxs-lookup"><span data-stu-id="ebd8a-120">You specify the path to an application `.dll` file to run the application.</span></span> <span data-ttu-id="ebd8a-121">Na przykład `dotnet myapp.dll` uruchamia aplikację `myapp`.</span><span class="sxs-lookup"><span data-stu-id="ebd8a-121">For example, `dotnet myapp.dll` runs the `myapp` application.</span></span> <span data-ttu-id="ebd8a-122">Zobacz [wdrażanie aplikacji .NET Core](../deploying/index.md) , aby dowiedzieć się więcej na temat opcji wdrażania.</span><span class="sxs-lookup"><span data-stu-id="ebd8a-122">See [.NET Core application deployment](../deploying/index.md) to learn about deployment options.</span></span>

## <a name="options"></a><span data-ttu-id="ebd8a-123">Opcje</span><span class="sxs-lookup"><span data-stu-id="ebd8a-123">Options</span></span>

<span data-ttu-id="ebd8a-124">Różne opcje są dostępne dla `dotnet` samodzielne, na potrzeby uruchamiania polecenia i uruchamiania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="ebd8a-124">Different options are available for `dotnet` by itself, for running a command, and for running an application.</span></span>

### <a name="options-for-dotnet-by-itself"></a><span data-ttu-id="ebd8a-125">Opcje dla dotnet</span><span class="sxs-lookup"><span data-stu-id="ebd8a-125">Options for dotnet by itself</span></span>

<span data-ttu-id="ebd8a-126">Poniższe opcje są przeznaczone dla `dotnet`.</span><span class="sxs-lookup"><span data-stu-id="ebd8a-126">The following options are for `dotnet` by itself.</span></span> <span data-ttu-id="ebd8a-127">Na przykład `dotnet --info`.</span><span class="sxs-lookup"><span data-stu-id="ebd8a-127">For example, `dotnet --info`.</span></span> <span data-ttu-id="ebd8a-128">Drukują informacje o środowisku.</span><span class="sxs-lookup"><span data-stu-id="ebd8a-128">They print out information about the environment.</span></span>

- **`--info`**

  <span data-ttu-id="ebd8a-129">Drukuje szczegółowe informacje na temat instalacji programu .NET Core i środowiska maszynowego, takiego jak bieżący system operacyjny, i zatwierdzania SHA dla wersji .NET Core.</span><span class="sxs-lookup"><span data-stu-id="ebd8a-129">Prints out detailed information about a .NET Core installation and the machine environment, such as the current operating system, and commit SHA of the .NET Core version.</span></span>

- **`--version`**

  <span data-ttu-id="ebd8a-130">Drukuje używaną wersję zestaw .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="ebd8a-130">Prints out the version of the .NET Core SDK in use.</span></span>

- **`--list-runtimes`**

  <span data-ttu-id="ebd8a-131">Drukuje listę zainstalowanych środowiska uruchomieniowego platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="ebd8a-131">Prints out a list of the installed .NET Core runtimes.</span></span>

- **`--list-sdks`**

  <span data-ttu-id="ebd8a-132">Drukuje listę zainstalowanych zestawów SDK platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="ebd8a-132">Prints out a list of the installed .NET Core SDKs.</span></span>

- **`-h|--help`**

  <span data-ttu-id="ebd8a-133">Drukuje listę dostępnych poleceń.</span><span class="sxs-lookup"><span data-stu-id="ebd8a-133">Prints out a list of available commands.</span></span>

### <a name="sdk-options-for-running-a-command"></a><span data-ttu-id="ebd8a-134">Opcje zestawu SDK do uruchamiania polecenia</span><span class="sxs-lookup"><span data-stu-id="ebd8a-134">SDK options for running a command</span></span>

<span data-ttu-id="ebd8a-135">Poniższe opcje dotyczą `dotnet` z poleceniem.</span><span class="sxs-lookup"><span data-stu-id="ebd8a-135">The following options are for `dotnet` with a command.</span></span> <span data-ttu-id="ebd8a-136">Na przykład `dotnet build --help`.</span><span class="sxs-lookup"><span data-stu-id="ebd8a-136">For example, `dotnet build --help`.</span></span>

- **`-d|--diagnostics`**

  <span data-ttu-id="ebd8a-137">Włącza diagnostykę danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="ebd8a-137">Enables diagnostic output.</span></span>

- **`-v|--verbosity <LEVEL>`**

  <span data-ttu-id="ebd8a-138">Ustawia poziom szczegółowości polecenia.</span><span class="sxs-lookup"><span data-stu-id="ebd8a-138">Sets the verbosity level of the command.</span></span> <span data-ttu-id="ebd8a-139">Dozwolone wartości to `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`i `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="ebd8a-139">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="ebd8a-140">Nieobsługiwane w każdym poleceniu.</span><span class="sxs-lookup"><span data-stu-id="ebd8a-140">Not supported in every command.</span></span> <span data-ttu-id="ebd8a-141">Aby określić, czy ta opcja jest dostępna, zobacz określoną stronę poleceń.</span><span class="sxs-lookup"><span data-stu-id="ebd8a-141">See specific command page to determine if this option is available.</span></span>

- **`-h|--help`**

  <span data-ttu-id="ebd8a-142">Drukuje dokumentację dla danego polecenia, taką jak `dotnet build --help`.</span><span class="sxs-lookup"><span data-stu-id="ebd8a-142">Prints out documentation for a given command, such as `dotnet build --help`.</span></span>

- **`command options`**

  <span data-ttu-id="ebd8a-143">Każde polecenie definiuje opcje specyficzne dla tego polecenia.</span><span class="sxs-lookup"><span data-stu-id="ebd8a-143">Each command defines options specific to that command.</span></span> <span data-ttu-id="ebd8a-144">Listę dostępnych opcji można znaleźć na stronie z konkretnym poleceniem.</span><span class="sxs-lookup"><span data-stu-id="ebd8a-144">See specific command page for a list of available options.</span></span>

### <a name="runtime-options"></a><span data-ttu-id="ebd8a-145">Opcje środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="ebd8a-145">Runtime options</span></span>

<span data-ttu-id="ebd8a-146">Poniższe opcje są dostępne, gdy `dotnet` uruchamia aplikację.</span><span class="sxs-lookup"><span data-stu-id="ebd8a-146">The following options are available when `dotnet` runs an application.</span></span> <span data-ttu-id="ebd8a-147">Na przykład `dotnet myapp.dll --fx-version 3.1.1`.</span><span class="sxs-lookup"><span data-stu-id="ebd8a-147">For example, `dotnet myapp.dll --fx-version 3.1.1`.</span></span>

- **`--additionalprobingpath <PATH>`**

  <span data-ttu-id="ebd8a-148">Ścieżka zawierająca zasady i zestawy do sondowania.</span><span class="sxs-lookup"><span data-stu-id="ebd8a-148">Path containing probing policy and assemblies to probe.</span></span>

- **`--additional-deps <PATH>`**

  <span data-ttu-id="ebd8a-149">Ścieżka do dodatkowego pliku *. deps. JSON* .</span><span class="sxs-lookup"><span data-stu-id="ebd8a-149">Path to an additional *.deps.json* file.</span></span> <span data-ttu-id="ebd8a-150">Plik *deps. JSON* zawiera listę zależności, zależności kompilacji i informacje o wersji używane do rozwiązywania konfliktów zestawów.</span><span class="sxs-lookup"><span data-stu-id="ebd8a-150">A *deps.json* file contains a list of dependencies, compilation dependencies, and version information used to address assembly conflicts.</span></span> <span data-ttu-id="ebd8a-151">Aby uzyskać więcej informacji, zobacz [pliki konfiguracji środowiska uruchomieniowego](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md) w serwisie GitHub.</span><span class="sxs-lookup"><span data-stu-id="ebd8a-151">For more information, see [Runtime Configuration Files](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md) on GitHub.</span></span>

- **`--fx-version <VERSION>`**

  <span data-ttu-id="ebd8a-152">Wersja środowiska uruchomieniowego platformy .NET Core do użycia w celu uruchomienia aplikacji.</span><span class="sxs-lookup"><span data-stu-id="ebd8a-152">Version of the .NET Core runtime to use to run the application.</span></span>

- **`--runtimeconfig`**

  <span data-ttu-id="ebd8a-153">Ścieżka do pliku *runtimeconfig. JSON* .</span><span class="sxs-lookup"><span data-stu-id="ebd8a-153">Path to a *runtimeconfig.json* file.</span></span> <span data-ttu-id="ebd8a-154">Plik *runtimeconfig. JSON* to plik konfiguracji, który zawiera ustawienia czasu wykonywania.</span><span class="sxs-lookup"><span data-stu-id="ebd8a-154">A *runtimeconfig.json* file is a configuration file that contains run-time settings.</span></span> <span data-ttu-id="ebd8a-155">Aby uzyskać więcej informacji, zobacz [Ustawienia konfiguracji środowiska uruchomieniowego .NET Core](../run-time-config/index.md#runtimeconfigjson).</span><span class="sxs-lookup"><span data-stu-id="ebd8a-155">For more information, see [.NET Core run-time configuration settings](../run-time-config/index.md#runtimeconfigjson).</span></span>

- <span data-ttu-id="ebd8a-156">**`--roll-forward-on-no-candidate-fx <N>`** **dostępne w zestawie SDK platformy .NET Core 2. x.**</span><span class="sxs-lookup"><span data-stu-id="ebd8a-156">**`--roll-forward-on-no-candidate-fx <N>`** **Available in .NET Core 2.x SDK.**</span></span>

  <span data-ttu-id="ebd8a-157">Definiuje zachowanie, gdy wymagana architektura udostępniona jest niedostępna.</span><span class="sxs-lookup"><span data-stu-id="ebd8a-157">Defines behavior when the required shared framework is not available.</span></span> <span data-ttu-id="ebd8a-158">`N` mogą być następujące:</span><span class="sxs-lookup"><span data-stu-id="ebd8a-158">`N` can be:</span></span>

  - <span data-ttu-id="ebd8a-159">`0` — Wyłącz nawet dodatkową wersję pomocniczą.</span><span class="sxs-lookup"><span data-stu-id="ebd8a-159">`0` - Disable even minor version roll forward.</span></span>
  - <span data-ttu-id="ebd8a-160">`1` — przewinięcie do wersji pomocniczej, ale nie w wersji głównej.</span><span class="sxs-lookup"><span data-stu-id="ebd8a-160">`1` - Roll forward on minor version, but not on major version.</span></span> <span data-ttu-id="ebd8a-161">Jest to zachowanie domyślne.</span><span class="sxs-lookup"><span data-stu-id="ebd8a-161">This is the default behavior.</span></span>
  - <span data-ttu-id="ebd8a-162">`2` — przewinięcie w przód do wersji pomocniczych i głównych.</span><span class="sxs-lookup"><span data-stu-id="ebd8a-162">`2` - Roll forward on minor and major versions.</span></span>

   <span data-ttu-id="ebd8a-163">Aby uzyskać więcej informacji, zobacz [przewinięcie do przodu](../whats-new/dotnet-core-2-1.md#roll-forward).</span><span class="sxs-lookup"><span data-stu-id="ebd8a-163">For more information, see [Roll forward](../whats-new/dotnet-core-2-1.md#roll-forward).</span></span>

- <span data-ttu-id="ebd8a-164">**`--roll-forward <SETTING>`** **dostępne od zestaw .NET Core SDK 3,0.**</span><span class="sxs-lookup"><span data-stu-id="ebd8a-164">**`--roll-forward <SETTING>`** **Available starting with .NET Core SDK 3.0.**</span></span>

  <span data-ttu-id="ebd8a-165">Kontroluje sposób, w jaki do aplikacji jest stosowane przewinięcie do przodu.</span><span class="sxs-lookup"><span data-stu-id="ebd8a-165">Controls how roll forward is applied to the app.</span></span> <span data-ttu-id="ebd8a-166">`SETTING` może być jedną z następujących wartości.</span><span class="sxs-lookup"><span data-stu-id="ebd8a-166">The `SETTING` can be one of the following values.</span></span> <span data-ttu-id="ebd8a-167">Jeśli nie zostanie określony, `Minor` jest wartością domyślną.</span><span class="sxs-lookup"><span data-stu-id="ebd8a-167">If not specified, `Minor` is the default.</span></span>

  - <span data-ttu-id="ebd8a-168">`LatestPatch` — przewinięcie do najwyższej wersji poprawki.</span><span class="sxs-lookup"><span data-stu-id="ebd8a-168">`LatestPatch` - Roll forward to the highest patch version.</span></span> <span data-ttu-id="ebd8a-169">Spowoduje to wyłączenie wycofywania wersji pomocniczej.</span><span class="sxs-lookup"><span data-stu-id="ebd8a-169">This disables minor version roll forward.</span></span>
  - <span data-ttu-id="ebd8a-170">`Minor` — przewinięcie do najmniejszej wyższej wersji pomocniczej, jeśli brakuje wymaganej wersji pomocniczej.</span><span class="sxs-lookup"><span data-stu-id="ebd8a-170">`Minor` - Roll forward to the lowest higher minor version, if requested minor version is missing.</span></span> <span data-ttu-id="ebd8a-171">Jeśli jest obecna żądana wersja pomocnicza, zostaną użyte zasady LatestPatch.</span><span class="sxs-lookup"><span data-stu-id="ebd8a-171">If the requested minor version is present, then the LatestPatch policy is used.</span></span>
  - <span data-ttu-id="ebd8a-172">`Major` — przewinięcie do najmniejszej wyższej wersji głównej i najniższej wersji pomocniczej, jeśli brakuje żądanej wersji głównej.</span><span class="sxs-lookup"><span data-stu-id="ebd8a-172">`Major` - Roll forward to lowest higher major version, and lowest minor version, if requested major version is missing.</span></span> <span data-ttu-id="ebd8a-173">Jeśli jest obecna żądana wersja główna, są używane zasady pomocnicze.</span><span class="sxs-lookup"><span data-stu-id="ebd8a-173">If the requested major version is present, then the Minor policy is used.</span></span>
  - <span data-ttu-id="ebd8a-174">`LatestMinor` — przewinięcie do najnowszej wersji pomocniczej, nawet jeśli jest obecna żądana wersja pomocnicza.</span><span class="sxs-lookup"><span data-stu-id="ebd8a-174">`LatestMinor` - Roll forward to highest minor version, even if requested minor version is present.</span></span> <span data-ttu-id="ebd8a-175">Przeznaczone do scenariuszy hostingu składników.</span><span class="sxs-lookup"><span data-stu-id="ebd8a-175">Intended for component hosting scenarios.</span></span>
  - <span data-ttu-id="ebd8a-176">`LatestMajor` — przewinięcie do przodu do najwyższej głównej i najwyższej wersji pomocniczej, nawet jeśli zażądana główna wersja jest obecna.</span><span class="sxs-lookup"><span data-stu-id="ebd8a-176">`LatestMajor` - Roll forward to highest major and highest minor version, even if requested major is present.</span></span> <span data-ttu-id="ebd8a-177">Przeznaczone do scenariuszy hostingu składników.</span><span class="sxs-lookup"><span data-stu-id="ebd8a-177">Intended for component hosting scenarios.</span></span>
  - <span data-ttu-id="ebd8a-178">`Disable` — nie przetaczaj dalej.</span><span class="sxs-lookup"><span data-stu-id="ebd8a-178">`Disable` - Don't roll forward.</span></span> <span data-ttu-id="ebd8a-179">Powiąż tylko z określoną wersją.</span><span class="sxs-lookup"><span data-stu-id="ebd8a-179">Only bind to specified version.</span></span> <span data-ttu-id="ebd8a-180">Te zasady nie są zalecane do użytku ogólnego, ponieważ uniemożliwiają one przekazanie do najnowszych poprawek.</span><span class="sxs-lookup"><span data-stu-id="ebd8a-180">This policy isn't recommended for general use because it disables the ability to roll forward to the latest patches.</span></span> <span data-ttu-id="ebd8a-181">Ta wartość jest zalecana tylko do celów testowych.</span><span class="sxs-lookup"><span data-stu-id="ebd8a-181">This value is only recommended for testing.</span></span>

<span data-ttu-id="ebd8a-182">Z wyjątkiem `Disable`, wszystkie ustawienia będą używać najwyższej dostępnej wersji poprawki.</span><span class="sxs-lookup"><span data-stu-id="ebd8a-182">With the exception of `Disable`, all settings will use the highest available patch version.</span></span>

<span data-ttu-id="ebd8a-183">Zachowanie przewinięcie do przodu można także skonfigurować we właściwościach pliku projektu, właściwości pliku konfiguracji czasu wykonywania i zmiennej środowiskowej.</span><span class="sxs-lookup"><span data-stu-id="ebd8a-183">Roll forward behavior can also be configured in a project file property, a run-time configuration file property, and an environment variable.</span></span> <span data-ttu-id="ebd8a-184">Aby uzyskać więcej informacji, zobacz [wersja główna środowiska uruchomieniowego do przodu](../whats-new/dotnet-core-3-0.md#major-version-runtime-roll-forward).</span><span class="sxs-lookup"><span data-stu-id="ebd8a-184">For more information, see [Major-version runtime roll forward](../whats-new/dotnet-core-3-0.md#major-version-runtime-roll-forward).</span></span>

## <a name="dotnet-commands"></a><span data-ttu-id="ebd8a-185">Polecenia dotnet</span><span class="sxs-lookup"><span data-stu-id="ebd8a-185">dotnet commands</span></span>

### <a name="general"></a><span data-ttu-id="ebd8a-186">Ogólne</span><span class="sxs-lookup"><span data-stu-id="ebd8a-186">General</span></span>

| <span data-ttu-id="ebd8a-187">Polecenie</span><span class="sxs-lookup"><span data-stu-id="ebd8a-187">Command</span></span>                                       | <span data-ttu-id="ebd8a-188">Funkcja</span><span class="sxs-lookup"><span data-stu-id="ebd8a-188">Function</span></span>                                                            |
| --------------------------------------------- | ------------------------------------------------------------------- |
| [<span data-ttu-id="ebd8a-189">dotnet build</span><span class="sxs-lookup"><span data-stu-id="ebd8a-189">dotnet build</span></span>](dotnet-build.md)               | <span data-ttu-id="ebd8a-190">Kompiluje aplikację platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="ebd8a-190">Builds a .NET Core application.</span></span>                                     |
| [<span data-ttu-id="ebd8a-191">dotnet build-server</span><span class="sxs-lookup"><span data-stu-id="ebd8a-191">dotnet build-server</span></span>](dotnet-build-server.md) | <span data-ttu-id="ebd8a-192">Współdziała z serwerami uruchomionymi przez kompilację.</span><span class="sxs-lookup"><span data-stu-id="ebd8a-192">Interacts with servers started by a build.</span></span>                          |
| [<span data-ttu-id="ebd8a-193">dotnet clean</span><span class="sxs-lookup"><span data-stu-id="ebd8a-193">dotnet clean</span></span>](dotnet-clean.md)               | <span data-ttu-id="ebd8a-194">Czyste dane wyjściowe kompilacji.</span><span class="sxs-lookup"><span data-stu-id="ebd8a-194">Clean build outputs.</span></span>                                                |
| [<span data-ttu-id="ebd8a-195">dotnet help</span><span class="sxs-lookup"><span data-stu-id="ebd8a-195">dotnet help</span></span>](dotnet-help.md)                 | <span data-ttu-id="ebd8a-196">Przedstawia bardziej szczegółową dokumentację dla polecenia w trybie online.</span><span class="sxs-lookup"><span data-stu-id="ebd8a-196">Shows more detailed documentation online for the command.</span></span>           |
| [<span data-ttu-id="ebd8a-197">dotnet migrate</span><span class="sxs-lookup"><span data-stu-id="ebd8a-197">dotnet migrate</span></span>](dotnet-migrate.md)           | <span data-ttu-id="ebd8a-198">Migruje prawidłowy projekt w wersji zapoznawczej 2 do projektu zestaw .NET Core SDK 1,0.</span><span class="sxs-lookup"><span data-stu-id="ebd8a-198">Migrates a valid Preview 2 project to a .NET Core SDK 1.0 project.</span></span>  |
| [<span data-ttu-id="ebd8a-199">dotnet msbuild</span><span class="sxs-lookup"><span data-stu-id="ebd8a-199">dotnet msbuild</span></span>](dotnet-msbuild.md)           | <span data-ttu-id="ebd8a-200">Zapewnia dostęp do wiersza polecenia programu MSBuild.</span><span class="sxs-lookup"><span data-stu-id="ebd8a-200">Provides access to the MSBuild command line.</span></span>                        |
| [<span data-ttu-id="ebd8a-201">dotnet new</span><span class="sxs-lookup"><span data-stu-id="ebd8a-201">dotnet new</span></span>](dotnet-new.md)                   | <span data-ttu-id="ebd8a-202">Inicjuje projekt C# lub F# dla danego szablonu.</span><span class="sxs-lookup"><span data-stu-id="ebd8a-202">Initializes a C# or F# project for a given template.</span></span>                |
| [<span data-ttu-id="ebd8a-203">dotnet pack</span><span class="sxs-lookup"><span data-stu-id="ebd8a-203">dotnet pack</span></span>](dotnet-pack.md)                 | <span data-ttu-id="ebd8a-204">Tworzy pakiet NuGet kodu.</span><span class="sxs-lookup"><span data-stu-id="ebd8a-204">Creates a NuGet package of your code.</span></span>                               |
| [<span data-ttu-id="ebd8a-205">dotnet publish</span><span class="sxs-lookup"><span data-stu-id="ebd8a-205">dotnet publish</span></span>](dotnet-publish.md)           | <span data-ttu-id="ebd8a-206">Publikuje zależne od programu .NET Framework lub samodzielną aplikację.</span><span class="sxs-lookup"><span data-stu-id="ebd8a-206">Publishes a .NET framework-dependent or self-contained application.</span></span> |
| [<span data-ttu-id="ebd8a-207">dotnet restore</span><span class="sxs-lookup"><span data-stu-id="ebd8a-207">dotnet restore</span></span>](dotnet-restore.md)           | <span data-ttu-id="ebd8a-208">Przywraca zależności dla danej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="ebd8a-208">Restores the dependencies for a given application.</span></span>                  |
| [<span data-ttu-id="ebd8a-209">dotnet run</span><span class="sxs-lookup"><span data-stu-id="ebd8a-209">dotnet run</span></span>](dotnet-run.md)                   | <span data-ttu-id="ebd8a-210">Uruchamia aplikację ze źródła.</span><span class="sxs-lookup"><span data-stu-id="ebd8a-210">Runs the application from source.</span></span>                                   |
| [<span data-ttu-id="ebd8a-211">dotnet sln</span><span class="sxs-lookup"><span data-stu-id="ebd8a-211">dotnet sln</span></span>](dotnet-sln.md)                   | <span data-ttu-id="ebd8a-212">Opcje dodawania, usuwania i wyświetlania listy projektów w pliku rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="ebd8a-212">Options to add, remove, and list projects in a solution file.</span></span>       |
| [<span data-ttu-id="ebd8a-213">dotnet store</span><span class="sxs-lookup"><span data-stu-id="ebd8a-213">dotnet store</span></span>](dotnet-store.md)               | <span data-ttu-id="ebd8a-214">Przechowuje zestawy w magazynie pakietów środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="ebd8a-214">Stores assemblies in the runtime package store.</span></span>                     |
| [<span data-ttu-id="ebd8a-215">dotnet test</span><span class="sxs-lookup"><span data-stu-id="ebd8a-215">dotnet test</span></span>](dotnet-test.md)                 | <span data-ttu-id="ebd8a-216">Uruchamia testy przy użyciu modułu uruchamiającego testy.</span><span class="sxs-lookup"><span data-stu-id="ebd8a-216">Runs tests using a test runner.</span></span>                                     |

### <a name="project-references"></a><span data-ttu-id="ebd8a-217">Odwołania projektu</span><span class="sxs-lookup"><span data-stu-id="ebd8a-217">Project references</span></span>

<span data-ttu-id="ebd8a-218">Polecenie</span><span class="sxs-lookup"><span data-stu-id="ebd8a-218">Command</span></span> | <span data-ttu-id="ebd8a-219">Funkcja</span><span class="sxs-lookup"><span data-stu-id="ebd8a-219">Function</span></span>
--- | ---
[<span data-ttu-id="ebd8a-220">dotnet add reference</span><span class="sxs-lookup"><span data-stu-id="ebd8a-220">dotnet add reference</span></span>](dotnet-add-reference.md) | <span data-ttu-id="ebd8a-221">Dodaje odwołanie do projektu.</span><span class="sxs-lookup"><span data-stu-id="ebd8a-221">Adds a project reference.</span></span>
[<span data-ttu-id="ebd8a-222">dotnet list reference</span><span class="sxs-lookup"><span data-stu-id="ebd8a-222">dotnet list reference</span></span>](dotnet-list-reference.md) | <span data-ttu-id="ebd8a-223">Wyświetla listę odwołań do projektu.</span><span class="sxs-lookup"><span data-stu-id="ebd8a-223">Lists project references.</span></span>
[<span data-ttu-id="ebd8a-224">dotnet remove reference</span><span class="sxs-lookup"><span data-stu-id="ebd8a-224">dotnet remove reference</span></span>](dotnet-remove-reference.md) | <span data-ttu-id="ebd8a-225">Usuwa odwołanie do projektu.</span><span class="sxs-lookup"><span data-stu-id="ebd8a-225">Removes a project reference.</span></span>

### <a name="nuget-packages"></a><span data-ttu-id="ebd8a-226">Pakiety NuGet</span><span class="sxs-lookup"><span data-stu-id="ebd8a-226">NuGet packages</span></span>

<span data-ttu-id="ebd8a-227">Polecenie</span><span class="sxs-lookup"><span data-stu-id="ebd8a-227">Command</span></span> | <span data-ttu-id="ebd8a-228">Funkcja</span><span class="sxs-lookup"><span data-stu-id="ebd8a-228">Function</span></span>
--- | ---
[<span data-ttu-id="ebd8a-229">dotnet add package</span><span class="sxs-lookup"><span data-stu-id="ebd8a-229">dotnet add package</span></span>](dotnet-add-package.md) | <span data-ttu-id="ebd8a-230">Dodaje pakiet NuGet.</span><span class="sxs-lookup"><span data-stu-id="ebd8a-230">Adds a NuGet package.</span></span>
[<span data-ttu-id="ebd8a-231">dotnet remove package</span><span class="sxs-lookup"><span data-stu-id="ebd8a-231">dotnet remove package</span></span>](dotnet-remove-package.md) | <span data-ttu-id="ebd8a-232">Usuwa pakiet NuGet.</span><span class="sxs-lookup"><span data-stu-id="ebd8a-232">Removes a NuGet package.</span></span>

### <a name="nuget-commands"></a><span data-ttu-id="ebd8a-233">Polecenia NuGet</span><span class="sxs-lookup"><span data-stu-id="ebd8a-233">NuGet commands</span></span>

<span data-ttu-id="ebd8a-234">Polecenie</span><span class="sxs-lookup"><span data-stu-id="ebd8a-234">Command</span></span> | <span data-ttu-id="ebd8a-235">Funkcja</span><span class="sxs-lookup"><span data-stu-id="ebd8a-235">Function</span></span>
--- | ---
[<span data-ttu-id="ebd8a-236">dotnet nuget delete</span><span class="sxs-lookup"><span data-stu-id="ebd8a-236">dotnet nuget delete</span></span>](dotnet-nuget-delete.md) | <span data-ttu-id="ebd8a-237">Usuwa pakiet z serwera lub go wystawia.</span><span class="sxs-lookup"><span data-stu-id="ebd8a-237">Deletes or unlists a package from the server.</span></span>
[<span data-ttu-id="ebd8a-238">dotnet nuget locals</span><span class="sxs-lookup"><span data-stu-id="ebd8a-238">dotnet nuget locals</span></span>](dotnet-nuget-locals.md) | <span data-ttu-id="ebd8a-239">Czyści lub wyświetla lokalne zasoby NuGet, takie jak pamięć podręczna żądań HTTP, tymczasowa pamięć podręczna lub folder pakietów globalnych dla całego komputera.</span><span class="sxs-lookup"><span data-stu-id="ebd8a-239">Clears or lists local NuGet resources such as http-request cache, temporary cache, or machine-wide global packages folder.</span></span>
[<span data-ttu-id="ebd8a-240">dotnet nuget push</span><span class="sxs-lookup"><span data-stu-id="ebd8a-240">dotnet nuget push</span></span>](dotnet-nuget-push.md) | <span data-ttu-id="ebd8a-241">Wypchnij pakiet na serwer i opublikuje go.</span><span class="sxs-lookup"><span data-stu-id="ebd8a-241">Pushes a package to the server and publishes it.</span></span>

### <a name="global-tool-path-and-local-tools-commands"></a><span data-ttu-id="ebd8a-242">Globalne, ścieżki narzędziowe i polecenia narzędzi lokalnych</span><span class="sxs-lookup"><span data-stu-id="ebd8a-242">Global, tool-path, and local tools commands</span></span>

<span data-ttu-id="ebd8a-243">Narzędzia są aplikacjami konsolowymi, które są instalowane z pakietów NuGet i są wywoływane z wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="ebd8a-243">Tools are console applications that are installed from NuGet packages and are invoked from the command prompt.</span></span> <span data-ttu-id="ebd8a-244">Narzędzia można pisać samodzielnie lub instalować Narzędzia zapisane przez inne firmy.</span><span class="sxs-lookup"><span data-stu-id="ebd8a-244">You can write tools yourself or install tools written by third parties.</span></span> <span data-ttu-id="ebd8a-245">Narzędzia są również nazywane narzędziami globalnymi, narzędziami ścieżki narzędzi i narzędziami lokalnymi.</span><span class="sxs-lookup"><span data-stu-id="ebd8a-245">Tools are also known as global tools, tool-path tools, and local tools.</span></span> <span data-ttu-id="ebd8a-246">Aby uzyskać więcej informacji, zobacz [Narzędzia platformy .NET Core — Omówienie](global-tools.md).</span><span class="sxs-lookup"><span data-stu-id="ebd8a-246">For more information, see [.NET Core tools overview](global-tools.md).</span></span> <span data-ttu-id="ebd8a-247">Narzędzia globalne i ścieżki narzędzi są dostępne począwszy od zestaw .NET Core SDK 2,1.</span><span class="sxs-lookup"><span data-stu-id="ebd8a-247">Global and tool-path tools are available starting with .NET Core SDK 2.1.</span></span> <span data-ttu-id="ebd8a-248">Narzędzia lokalne są dostępne począwszy od zestaw .NET Core SDK 3,0.</span><span class="sxs-lookup"><span data-stu-id="ebd8a-248">Local tools are available starting with .NET Core SDK 3.0.</span></span>

<span data-ttu-id="ebd8a-249">Polecenie</span><span class="sxs-lookup"><span data-stu-id="ebd8a-249">Command</span></span> | <span data-ttu-id="ebd8a-250">Funkcja</span><span class="sxs-lookup"><span data-stu-id="ebd8a-250">Function</span></span>
--- | ---
[<span data-ttu-id="ebd8a-251">dotnet tool install</span><span class="sxs-lookup"><span data-stu-id="ebd8a-251">dotnet tool install</span></span>](dotnet-tool-install.md) | <span data-ttu-id="ebd8a-252">Instaluje narzędzie na komputerze.</span><span class="sxs-lookup"><span data-stu-id="ebd8a-252">Installs a tool on your machine.</span></span>
[<span data-ttu-id="ebd8a-253">dotnet tool list</span><span class="sxs-lookup"><span data-stu-id="ebd8a-253">dotnet tool list</span></span>](dotnet-tool-list.md) | <span data-ttu-id="ebd8a-254">Wyświetla listę wszystkich globalnych narzędzi, ścieżek narzędziowych lub lokalnych zainstalowanych obecnie na komputerze.</span><span class="sxs-lookup"><span data-stu-id="ebd8a-254">Lists all global, tool-path, or local tools currently installed on your machine.</span></span>
[<span data-ttu-id="ebd8a-255">dotnet tool uninstall</span><span class="sxs-lookup"><span data-stu-id="ebd8a-255">dotnet tool uninstall</span></span>](dotnet-tool-uninstall.md) | <span data-ttu-id="ebd8a-256">Odinstalowuje narzędzie z komputera.</span><span class="sxs-lookup"><span data-stu-id="ebd8a-256">Uninstalls a tool from your machine.</span></span>
[<span data-ttu-id="ebd8a-257">dotnet tool update</span><span class="sxs-lookup"><span data-stu-id="ebd8a-257">dotnet tool update</span></span>](dotnet-tool-update.md) | <span data-ttu-id="ebd8a-258">Aktualizuje narzędzie zainstalowane na komputerze.</span><span class="sxs-lookup"><span data-stu-id="ebd8a-258">Updates a tool that is installed on your machine.</span></span>

### <a name="additional-tools"></a><span data-ttu-id="ebd8a-259">Dodatkowe narzędzia</span><span class="sxs-lookup"><span data-stu-id="ebd8a-259">Additional tools</span></span>

<span data-ttu-id="ebd8a-260">Począwszy od zestaw .NET Core SDK 2.1.300, wiele narzędzi, które były dostępne tylko dla poszczególnych projektów, przy użyciu `DotnetCliToolReference`, są teraz dostępne jako część zestaw .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="ebd8a-260">Starting with .NET Core SDK 2.1.300, a number of tools that were available only on a per project basis using `DotnetCliToolReference` are now available as part of the .NET Core SDK.</span></span> <span data-ttu-id="ebd8a-261">Te narzędzia są wymienione w poniższej tabeli:</span><span class="sxs-lookup"><span data-stu-id="ebd8a-261">These tools are listed in the following table:</span></span>

| <span data-ttu-id="ebd8a-262">Narzędzie</span><span class="sxs-lookup"><span data-stu-id="ebd8a-262">Tool</span></span>                                              | <span data-ttu-id="ebd8a-263">Funkcja</span><span class="sxs-lookup"><span data-stu-id="ebd8a-263">Function</span></span>                                                     |
| ------------------------------------------------- | ------------------------------------------------------------ |
| <span data-ttu-id="ebd8a-264">dev-certs</span><span class="sxs-lookup"><span data-stu-id="ebd8a-264">dev-certs</span></span>                                         | <span data-ttu-id="ebd8a-265">Tworzy i zarządza certyfikatami deweloperskimi.</span><span class="sxs-lookup"><span data-stu-id="ebd8a-265">Creates and manages development certificates.</span></span>                |
| [<span data-ttu-id="ebd8a-266">bieżąco</span><span class="sxs-lookup"><span data-stu-id="ebd8a-266">ef</span></span>](/ef/core/miscellaneous/cli/dotnet)           | <span data-ttu-id="ebd8a-267">Entity Framework Core narzędzia wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="ebd8a-267">Entity Framework Core command-line tools.</span></span>                    |
| <span data-ttu-id="ebd8a-268">SQL-pamięć podręczna</span><span class="sxs-lookup"><span data-stu-id="ebd8a-268">sql-cache</span></span>                                         | <span data-ttu-id="ebd8a-269">SQL Server narzędzia wiersza polecenia pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="ebd8a-269">SQL Server cache command-line tools.</span></span>                         |
| [<span data-ttu-id="ebd8a-270">wpisy tajne użytkownika</span><span class="sxs-lookup"><span data-stu-id="ebd8a-270">user-secrets</span></span>](/aspnet/core/security/app-secrets) | <span data-ttu-id="ebd8a-271">Zarządza kluczami tajnymi użytkowników deweloperskich.</span><span class="sxs-lookup"><span data-stu-id="ebd8a-271">Manages development user secrets.</span></span>                            |
| [<span data-ttu-id="ebd8a-272">Obejrzyj</span><span class="sxs-lookup"><span data-stu-id="ebd8a-272">watch</span></span>](/aspnet/core/tutorials/dotnet-watch)      | <span data-ttu-id="ebd8a-273">Uruchamia obserwatora plików, który uruchamia polecenie, gdy pliki zmienią się.</span><span class="sxs-lookup"><span data-stu-id="ebd8a-273">Starts a file watcher that runs a command when files change.</span></span> |

<span data-ttu-id="ebd8a-274">Aby uzyskać więcej informacji na temat każdego narzędzia, wpisz `dotnet <tool-name> --help`.</span><span class="sxs-lookup"><span data-stu-id="ebd8a-274">For more information about each tool, type `dotnet <tool-name> --help`.</span></span>

## <a name="examples"></a><span data-ttu-id="ebd8a-275">Przykłady</span><span class="sxs-lookup"><span data-stu-id="ebd8a-275">Examples</span></span>

<span data-ttu-id="ebd8a-276">Utwórz nową aplikację konsolową platformy .NET Core:</span><span class="sxs-lookup"><span data-stu-id="ebd8a-276">Create a new .NET Core console application:</span></span>

```dotnetcli
dotnet new console
```

<span data-ttu-id="ebd8a-277">Kompiluj projekt i jego zależności w danym katalogu:</span><span class="sxs-lookup"><span data-stu-id="ebd8a-277">Build a project and its dependencies in a given directory:</span></span>

```dotnetcli
dotnet build
```

<span data-ttu-id="ebd8a-278">Uruchom aplikację:</span><span class="sxs-lookup"><span data-stu-id="ebd8a-278">Run an application:</span></span>

```dotnetcli
dotnet myapp.dll
```

## <a name="environment-variables"></a><span data-ttu-id="ebd8a-279">Zmienne środowiskowe</span><span class="sxs-lookup"><span data-stu-id="ebd8a-279">Environment variables</span></span>

- <span data-ttu-id="ebd8a-280">`DOTNET_ROOT`, `DOTNET_ROOT(x86)`</span><span class="sxs-lookup"><span data-stu-id="ebd8a-280">`DOTNET_ROOT`, `DOTNET_ROOT(x86)`</span></span>

  <span data-ttu-id="ebd8a-281">Określa lokalizację środowiska uruchomieniowego programu .NET Core, jeśli nie są one zainstalowane w domyślnej lokalizacji.</span><span class="sxs-lookup"><span data-stu-id="ebd8a-281">Specifies the location of the .NET Core runtimes, if they are not installed in the default location.</span></span> <span data-ttu-id="ebd8a-282">Domyślną lokalizacją w systemie Windows jest `C:\Program Files\dotnet`.</span><span class="sxs-lookup"><span data-stu-id="ebd8a-282">The default location on Windows is `C:\Program Files\dotnet`.</span></span> <span data-ttu-id="ebd8a-283">Domyślną lokalizacją w systemie Linux i macOS jest `/usr/share/dotnet`.</span><span class="sxs-lookup"><span data-stu-id="ebd8a-283">The default location on Linux and macOS is `/usr/share/dotnet`.</span></span> <span data-ttu-id="ebd8a-284">Ta zmienna środowiskowa jest używana tylko w przypadku uruchamiania aplikacji za pośrednictwem wygenerowanych plików wykonywalnych (apphosts).</span><span class="sxs-lookup"><span data-stu-id="ebd8a-284">This environment variable is used only when running apps via generated executables (apphosts).</span></span> <span data-ttu-id="ebd8a-285">Zamiast tego użyto `DOTNET_ROOT(x86)` w przypadku uruchamiania 32-bitowego pliku wykonywalnego na 64-bitowym systemie operacyjnym.</span><span class="sxs-lookup"><span data-stu-id="ebd8a-285">`DOTNET_ROOT(x86)` is used instead when running a 32-bit executable on a 64-bit OS.</span></span>

- `DOTNET_PACKAGES`

  <span data-ttu-id="ebd8a-286">Folder pakiety globalne.</span><span class="sxs-lookup"><span data-stu-id="ebd8a-286">The global packages folder.</span></span> <span data-ttu-id="ebd8a-287">Jeśli nie zostanie ustawiona, domyślnie jest `~/.nuget/packages` w systemie UNIX lub `%userprofile%\.nuget\packages` na komputerze z systemem Windows.</span><span class="sxs-lookup"><span data-stu-id="ebd8a-287">If not set, it defaults to `~/.nuget/packages` on Unix or `%userprofile%\.nuget\packages` on Windows.</span></span>

- `DOTNET_SERVICING`

  <span data-ttu-id="ebd8a-288">Określa lokalizację indeksu obsługi, który ma być używany przez host udostępniony podczas ładowania środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="ebd8a-288">Specifies the location of the servicing index to use by the shared host when loading the runtime.</span></span>

- `DOTNET_CLI_TELEMETRY_OPTOUT`

  <span data-ttu-id="ebd8a-289">Określa, czy dane dotyczące użycia narzędzi .NET Core są zbierane i wysyłane do firmy Microsoft.</span><span class="sxs-lookup"><span data-stu-id="ebd8a-289">Specifies whether data about the .NET Core tools usage is collected and sent to Microsoft.</span></span> <span data-ttu-id="ebd8a-290">Ustaw `true`, aby zrezygnować z funkcji telemetrii (wartości `true`, `1`lub `yes` zaakceptowane).</span><span class="sxs-lookup"><span data-stu-id="ebd8a-290">Set to `true` to opt-out of the telemetry feature (values `true`, `1`, or `yes` accepted).</span></span> <span data-ttu-id="ebd8a-291">W przeciwnym razie ustaw wartość `false`, aby zrezygnować z funkcji telemetrii (wartości `false`, `0`lub `no` zaakceptowane).</span><span class="sxs-lookup"><span data-stu-id="ebd8a-291">Otherwise, set to `false` to opt into the telemetry features (values `false`, `0`, or `no` accepted).</span></span> <span data-ttu-id="ebd8a-292">Jeśli nie zostanie ustawiona, wartość domyślna to `false` i aktywna jest funkcja telemetrii.</span><span class="sxs-lookup"><span data-stu-id="ebd8a-292">If not set, the default is `false` and the telemetry feature is active.</span></span>

- `DOTNET_MULTILEVEL_LOOKUP`

  <span data-ttu-id="ebd8a-293">Określa, czy środowisko uruchomieniowe programu .NET Core, udostępnione środowisko lub zestaw SDK są rozpoznawane z lokalizacji globalnej.</span><span class="sxs-lookup"><span data-stu-id="ebd8a-293">Specifies whether .NET Core runtime, shared framework, or SDK are resolved from the global location.</span></span> <span data-ttu-id="ebd8a-294">Jeśli nie zostanie ustawiona, wartość domyślna to 1 (`true`logiczna).</span><span class="sxs-lookup"><span data-stu-id="ebd8a-294">If not set, it defaults to 1 (logical `true`).</span></span> <span data-ttu-id="ebd8a-295">Ustaw wartość 0 (logiczne `false`), aby nie rozwiązać z lokalizacji globalnej i uzyskać izolowanych instalacji platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="ebd8a-295">Set to 0 (logical `false`) to not resolve from the global location and have isolated .NET Core installations.</span></span> <span data-ttu-id="ebd8a-296">Aby uzyskać więcej informacji o wyszukiwaniu wielu poziomów, zobacz [SharedFX wyszukiwanie na wielu poziomach](https://github.com/dotnet/core-setup/blob/master/Documentation/design-docs/multilevel-sharedfx-lookup.md).</span><span class="sxs-lookup"><span data-stu-id="ebd8a-296">For more information about multi-level lookup, see [Multi-level SharedFX Lookup](https://github.com/dotnet/core-setup/blob/master/Documentation/design-docs/multilevel-sharedfx-lookup.md).</span></span>

- <span data-ttu-id="ebd8a-297">`DOTNET_ROLL_FORWARD` **dostępne począwszy od zestawu .NET Core 3. x SDK.**</span><span class="sxs-lookup"><span data-stu-id="ebd8a-297">`DOTNET_ROLL_FORWARD` **Available starting with .NET Core 3.x SDK.**</span></span>

  <span data-ttu-id="ebd8a-298">Określa zachowanie funkcji przyciągania do przodu.</span><span class="sxs-lookup"><span data-stu-id="ebd8a-298">Determines roll forward behavior.</span></span> <span data-ttu-id="ebd8a-299">Aby uzyskać więcej informacji, zobacz opcję `--roll-forward` wcześniej w tym artykule.</span><span class="sxs-lookup"><span data-stu-id="ebd8a-299">For more information, see the `--roll-forward` option earlier in this article.</span></span>

- <span data-ttu-id="ebd8a-300">`DOTNET_ROLL_FORWARD_ON_NO_CANDIDATE_FX` **dostępne w zestawie SDK platformy .NET Core 2. x.**</span><span class="sxs-lookup"><span data-stu-id="ebd8a-300">`DOTNET_ROLL_FORWARD_ON_NO_CANDIDATE_FX` **Available in .NET Core 2.x SDK.**</span></span>

  <span data-ttu-id="ebd8a-301">Wyłącza opcję wycofywania wersji pomocniczej, jeśli jest ustawiona na `0`.</span><span class="sxs-lookup"><span data-stu-id="ebd8a-301">Disables minor version roll forward, if set to `0`.</span></span> <span data-ttu-id="ebd8a-302">Aby uzyskać więcej informacji, zobacz [przewinięcie do przodu](../whats-new/dotnet-core-2-1.md#roll-forward).</span><span class="sxs-lookup"><span data-stu-id="ebd8a-302">For more information, see [Roll forward](../whats-new/dotnet-core-2-1.md#roll-forward).</span></span>

- `DOTNET_CLI_UI_LANGUAGE`

  <span data-ttu-id="ebd8a-303">Ustawia język interfejsu użytkownika CLI przy użyciu wartości ustawień regionalnych, takich jak `en-us`.</span><span class="sxs-lookup"><span data-stu-id="ebd8a-303">Sets the language of the CLI UI using a locale value such as `en-us`.</span></span> <span data-ttu-id="ebd8a-304">Obsługiwane wartości są takie same jak w przypadku programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="ebd8a-304">The supported values are the same as for Visual Studio.</span></span> <span data-ttu-id="ebd8a-305">Aby uzyskać więcej informacji, zobacz sekcję dotyczącą zmiany języka Instalatora w [dokumentacji instalacyjnej programu Visual Studio](https://docs.microsoft.com/visualstudio/install/install-visual-studio?view=vs-2019).</span><span class="sxs-lookup"><span data-stu-id="ebd8a-305">For more information, see the section on changing the installer language in the [Visual Studio installation documentation](https://docs.microsoft.com/visualstudio/install/install-visual-studio?view=vs-2019).</span></span> <span data-ttu-id="ebd8a-306">Reguły Menedżera zasobów platformy .NET mają zastosowanie, więc nie trzeba wybierać dokładnego dopasowania&mdash;można również wybrać elementy podrzędne w drzewie `CultureInfo`.</span><span class="sxs-lookup"><span data-stu-id="ebd8a-306">The .NET resource manager rules apply, so you don't have to pick an exact match&mdash;you can also pick descendants in the `CultureInfo` tree.</span></span> <span data-ttu-id="ebd8a-307">Na przykład jeśli ustawisz ją na `fr-CA`, interfejs wiersza polecenia znajdzie i użyje tłumaczeń `fr`.</span><span class="sxs-lookup"><span data-stu-id="ebd8a-307">For example, if you set it to `fr-CA`, the CLI will find and use the `fr` translations.</span></span> <span data-ttu-id="ebd8a-308">Jeśli ustawisz go na język, który nie jest obsługiwany, interfejs wiersza polecenia powróci do języka angielskiego.</span><span class="sxs-lookup"><span data-stu-id="ebd8a-308">If you set it to a language that is not supported, the CLI falls back to English.</span></span>

- `DOTNET_DISABLE_GUI_ERRORS`

  <span data-ttu-id="ebd8a-309">Dla plików wykonywalnych z włączoną obsługą graficznego interfejsu użytkownika — wyłącza okno podręczne, które zwykle jest wyświetlane dla niektórych klas błędów.</span><span class="sxs-lookup"><span data-stu-id="ebd8a-309">For GUI-enabled generated executables - disables dialog popup which normally shows for certain classes of errors.</span></span> <span data-ttu-id="ebd8a-310">Zapisuje tylko dane do `stderr` i opuszcza w tych przypadkach.</span><span class="sxs-lookup"><span data-stu-id="ebd8a-310">It only writes to `stderr` and exits in those cases.</span></span>
  
- `DOTNET_ADDITIONAL_DEPS`

  <span data-ttu-id="ebd8a-311">Odpowiednik opcji interfejsu wiersza polecenia `--additional-deps`.</span><span class="sxs-lookup"><span data-stu-id="ebd8a-311">Equivalent to CLI option `--additional-deps`.</span></span>

- `DOTNET_RUNTIME_ID`

  <span data-ttu-id="ebd8a-312">Zastępuje wykrytego identyfikatora RID.</span><span class="sxs-lookup"><span data-stu-id="ebd8a-312">Overrides the detected RID.</span></span>

- `DOTNET_SHARED_STORE`

  <span data-ttu-id="ebd8a-313">Lokalizacja "udostępnionego magazynu", do którego w niektórych przypadkach jest powracana rozdzielczość zestawu.</span><span class="sxs-lookup"><span data-stu-id="ebd8a-313">Location of the "shared store" which assembly resolution falls back to in some cases.</span></span>

- `DOTNET_STARTUP_HOOKS`

  <span data-ttu-id="ebd8a-314">Lista zestawów, z których mają zostać załadowane i wykonane uruchomienia.</span><span class="sxs-lookup"><span data-stu-id="ebd8a-314">List of assemblies to load and execute startup hooks from.</span></span>

- <span data-ttu-id="ebd8a-315">`COREHOST_TRACE`, `COREHOST_TRACEFILE`, `COREHOST_TRACE_VERBOSITY`</span><span class="sxs-lookup"><span data-stu-id="ebd8a-315">`COREHOST_TRACE`, `COREHOST_TRACEFILE`, `COREHOST_TRACE_VERBOSITY`</span></span>

  <span data-ttu-id="ebd8a-316">Steruje śledzeniem diagnostyki ze składników hostingowych, takich jak `dotnet.exe`, `hostfxr`i `hostpolicy`.</span><span class="sxs-lookup"><span data-stu-id="ebd8a-316">Controls diagnostics tracing from the hosting components, such as `dotnet.exe`, `hostfxr`, and `hostpolicy`.</span></span>

## <a name="see-also"></a><span data-ttu-id="ebd8a-317">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ebd8a-317">See also</span></span>

- [<span data-ttu-id="ebd8a-318">Pliki konfiguracji środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="ebd8a-318">Runtime Configuration Files</span></span>](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md)
- [<span data-ttu-id="ebd8a-319">Ustawienia konfiguracji środowiska uruchomieniowego .NET Core</span><span class="sxs-lookup"><span data-stu-id="ebd8a-319">.NET Core run-time configuration settings</span></span>](../run-time-config/index.md)
