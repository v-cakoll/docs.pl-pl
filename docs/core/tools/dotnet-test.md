---
title: polecenie test DotNet
description: Polecenia dotnet test służy do wykonywania testów jednostkowych w danym projekcie.
ms.date: 05/29/2018
ms.openlocfilehash: 6b67273f549edd7712237756a5aba13d5cb59a61
ms.sourcegitcommit: 52e588dc2ee74d484cd07ac60076be25cbf777ab
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/27/2019
ms.locfileid: "67410368"
---
# <a name="dotnet-test"></a><span data-ttu-id="efa93-103">dotnet test</span><span class="sxs-lookup"><span data-stu-id="efa93-103">dotnet test</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="efa93-104">Nazwa</span><span class="sxs-lookup"><span data-stu-id="efa93-104">Name</span></span>

<span data-ttu-id="efa93-105">`dotnet test` -Sterownik test .NET służących do wykonywania testów jednostkowych.</span><span class="sxs-lookup"><span data-stu-id="efa93-105">`dotnet test` - .NET test driver used to execute unit tests.</span></span>

## <a name="synopsis"></a><span data-ttu-id="efa93-106">Streszczenie</span><span class="sxs-lookup"><span data-stu-id="efa93-106">Synopsis</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="efa93-107">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="efa93-107">.NET Core 2.1</span></span>](#tab/netcore21)

```console
dotnet test [<PROJECT>] [-a|--test-adapter-path] [--blame] [-c|--configuration] [--collect] [-d|--diag] [-f|--framework] [--filter]
    [-l|--logger] [--no-build] [--no-restore] [-o|--output] [-r|--results-directory] [-s|--settings] [-t|--list-tests] 
    [-v|--verbosity] [-- <RunSettings arguments>]

dotnet test [-h|--help]
```

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="efa93-108">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="efa93-108">.NET Core 2.0</span></span>](#tab/netcore20)

```console
dotnet test [<PROJECT>] [-a|--test-adapter-path] [-c|--configuration] [--collect] [-d|--diag] [-f|--framework] [--filter]
    [-l|--logger] [--no-build] [--no-restore] [-o|--output] [-r|--results-directory] [-s|--settings] [-t|--list-tests] [-v|--verbosity]

dotnet test [-h|--help]
```

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="efa93-109">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="efa93-109">.NET Core 1.x</span></span>](#tab/netcore1x)

```console
dotnet test [<PROJECT>] [-a|--test-adapter-path] [-c|--configuration] [-d|--diag] [-f|--framework] [--filter] [-l|--logger] [--no-build] [-o|--output] [-s|--settings] [-t|--list-tests]  [-v|--verbosity]

dotnet test [-h|--help]
```

---

## <a name="description"></a><span data-ttu-id="efa93-110">Opis</span><span class="sxs-lookup"><span data-stu-id="efa93-110">Description</span></span>

<span data-ttu-id="efa93-111">`dotnet test` Polecenie służy do wykonywania testów jednostkowych w danym projekcie.</span><span class="sxs-lookup"><span data-stu-id="efa93-111">The `dotnet test` command is used to execute unit tests in a given project.</span></span> <span data-ttu-id="efa93-112">`dotnet test` Polecenie uruchamia aplikację konsolową modułu uruchamiającego test, określony dla projektu.</span><span class="sxs-lookup"><span data-stu-id="efa93-112">The `dotnet test` command launches the test runner console application specified for a project.</span></span> <span data-ttu-id="efa93-113">Moduł uruchamiający testy zdefiniowane dla środowiska testów jednostkowych (np. MSTest, NUnit lub xUnit) są wykonywane i zgłasza powodzenie lub niepowodzenie każdego testu.</span><span class="sxs-lookup"><span data-stu-id="efa93-113">The test runner executes the tests defined for a unit test framework (for example, MSTest, NUnit, or xUnit) and reports the success or failure of each test.</span></span> <span data-ttu-id="efa93-114">Jeśli wszystkie testy zakończą się powodzeniem, narzędzia test runner zwraca wartość 0, kod zakończenia; Jeśli dowolny test zakończy się niepowodzeniem, w przeciwnym razie zwraca 1.</span><span class="sxs-lookup"><span data-stu-id="efa93-114">If all tests are successful, the test runner returns 0 as an exit code; otherwise if any test fails, it returns 1.</span></span> <span data-ttu-id="efa93-115">Narzędzie test runner Biblioteka testów jednostkowych jest spakowany jako pakiety NuGet i zostaną przywrócone jako zwykłe zależności projektu.</span><span class="sxs-lookup"><span data-stu-id="efa93-115">The test runner and the unit test library are packaged as NuGet packages and are restored as ordinary dependencies for the project.</span></span>

<span data-ttu-id="efa93-116">Projekty testowe określić modułu uruchamiającego testy przy użyciu zwykłej `<PackageReference>` elementu, jak pokazano w poniższym przykładowym pliku projektu:</span><span class="sxs-lookup"><span data-stu-id="efa93-116">Test projects specify the test runner using an ordinary `<PackageReference>` element, as seen in the following sample project file:</span></span>

[!code-xml[XUnit Basic Template](../../../samples/snippets/csharp/xunit-test/xunit-test.csproj)]

## <a name="arguments"></a><span data-ttu-id="efa93-117">Argumenty</span><span class="sxs-lookup"><span data-stu-id="efa93-117">Arguments</span></span>

`PROJECT`

<span data-ttu-id="efa93-118">Ścieżka do projektu testowego.</span><span class="sxs-lookup"><span data-stu-id="efa93-118">Path to the test project.</span></span> <span data-ttu-id="efa93-119">Jeśli nie zostanie określony, domyślnie bieżącego katalogu.</span><span class="sxs-lookup"><span data-stu-id="efa93-119">If not specified, it defaults to current directory.</span></span>

## <a name="options"></a><span data-ttu-id="efa93-120">Opcje</span><span class="sxs-lookup"><span data-stu-id="efa93-120">Options</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="efa93-121">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="efa93-121">.NET Core 2.1</span></span>](#tab/netcore21)

`-a|--test-adapter-path <PATH_TO_ADAPTER>`

<span data-ttu-id="efa93-122">Używa niestandardowych adapterów testowych z określonej ścieżki w przebiegu testu.</span><span class="sxs-lookup"><span data-stu-id="efa93-122">Use the custom test adapters from the specified path in the test run.</span></span>

`--blame`

<span data-ttu-id="efa93-123">Uruchamia testy w trybie polecenia blame.</span><span class="sxs-lookup"><span data-stu-id="efa93-123">Runs the tests in blame mode.</span></span> <span data-ttu-id="efa93-124">Ta opcja jest przydatna polega na wyizolowaniu problematyczne testy, powodując hosta testów ulega awarii.</span><span class="sxs-lookup"><span data-stu-id="efa93-124">This option is helpful in isolating the problematic tests causing test host to crash.</span></span> <span data-ttu-id="efa93-125">Tworzy plik wyjściowy w bieżącym katalogu jako *Sequence.xml* , przechwytuje kolejność wykonywania testów przed awarią.</span><span class="sxs-lookup"><span data-stu-id="efa93-125">It creates an output file in the current directory as *Sequence.xml* that captures the order of tests execution before the crash.</span></span>

`-c|--configuration {Debug|Release}`

<span data-ttu-id="efa93-126">Definiuje konfigurację kompilacji.</span><span class="sxs-lookup"><span data-stu-id="efa93-126">Defines the build configuration.</span></span> <span data-ttu-id="efa93-127">Wartość domyślna to `Debug`, ale konfiguracji projektu można zastąpić to ustawienie SDK domyślne.</span><span class="sxs-lookup"><span data-stu-id="efa93-127">The default value is `Debug`, but your project's configuration could override this default SDK setting.</span></span>

`--collect <DATA_COLLECTOR_FRIENDLY_NAME>`

<span data-ttu-id="efa93-128">Włącza moduł zbierający dane dla przebiegu testu.</span><span class="sxs-lookup"><span data-stu-id="efa93-128">Enables data collector for the test run.</span></span> <span data-ttu-id="efa93-129">Aby uzyskać więcej informacji, zobacz [monitorowanie i analizowanie przebiegu testu](https://aka.ms/vstest-collect).</span><span class="sxs-lookup"><span data-stu-id="efa93-129">For more information, see [Monitor and analyze test run](https://aka.ms/vstest-collect).</span></span>

`-d|--diag <PATH_TO_DIAGNOSTICS_FILE>`

<span data-ttu-id="efa93-130">Włącza tryb diagnostycznych dla testu platformy i zapisu komunikaty diagnostyczne do określonego pliku.</span><span class="sxs-lookup"><span data-stu-id="efa93-130">Enables diagnostic mode for the test platform and write diagnostic messages to the specified file.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="efa93-131">Wyszukuje pliki binarne testu dla określonego [framework](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="efa93-131">Looks for test binaries for a specific [framework](../../standard/frameworks.md).</span></span>

`--filter <EXPRESSION>`

<span data-ttu-id="efa93-132">Filtruje testy w bieżącym projekcie za pomocą podanego wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="efa93-132">Filters out tests in the current project using the given expression.</span></span> <span data-ttu-id="efa93-133">Aby uzyskać więcej informacji, zobacz [szczegóły opcji filtru](#filter-option-details) sekcji.</span><span class="sxs-lookup"><span data-stu-id="efa93-133">For more information, see the [Filter option details](#filter-option-details) section.</span></span> <span data-ttu-id="efa93-134">Aby uzyskać dodatkowe informacje i przykłady dotyczące korzystania z jednostki selektywne testowanie filtrowania, zobacz [uruchamianie selektywnych testów jednostkowych](../testing/selective-unit-tests.md).</span><span class="sxs-lookup"><span data-stu-id="efa93-134">For more information and examples on how to use selective unit test filtering, see [Running selective unit tests](../testing/selective-unit-tests.md).</span></span>

`-h|--help`

<span data-ttu-id="efa93-135">Drukuje krótki pomoc dotyczącą polecenia.</span><span class="sxs-lookup"><span data-stu-id="efa93-135">Prints out a short help for the command.</span></span>

`-l|--logger <LoggerUri/FriendlyName>`

<span data-ttu-id="efa93-136">Określa Rejestrator dla wyników badań.</span><span class="sxs-lookup"><span data-stu-id="efa93-136">Specifies a logger for test results.</span></span>

`--no-build`

<span data-ttu-id="efa93-137">Nie da się skompilować projektu testowego przed jego uruchomieniem.</span><span class="sxs-lookup"><span data-stu-id="efa93-137">Doesn't build the test project before running it.</span></span> <span data-ttu-id="efa93-138">Ustawia ona również niejawne `--no-restore` flagi.</span><span class="sxs-lookup"><span data-stu-id="efa93-138">It also implicit sets the `--no-restore` flag.</span></span>

`--no-restore`

<span data-ttu-id="efa93-139">Przy uruchamianiu polecenia niejawne przywracania nie jest wykonywany.</span><span class="sxs-lookup"><span data-stu-id="efa93-139">Doesn't execute an implicit restore when running the command.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="efa93-140">Katalog, w którym można znaleźć plików binarnych do uruchomienia.</span><span class="sxs-lookup"><span data-stu-id="efa93-140">Directory in which to find the binaries to run.</span></span>

`-r|--results-directory <PATH>`

<span data-ttu-id="efa93-141">Katalog, gdzie wyników testu do umieszczenia.</span><span class="sxs-lookup"><span data-stu-id="efa93-141">The directory where the test results are going to be placed.</span></span> <span data-ttu-id="efa93-142">Jeśli określony katalog nie istnieje, zostanie utworzony.</span><span class="sxs-lookup"><span data-stu-id="efa93-142">If the specified directory doesn't exist, it's created.</span></span>

`-s|--settings <SETTINGS_FILE>`

<span data-ttu-id="efa93-143">`.runsettings` Plik używany do uruchamiania testów.</span><span class="sxs-lookup"><span data-stu-id="efa93-143">The `.runsettings` file to use for running the tests.</span></span> [<span data-ttu-id="efa93-144">Konfigurowanie testów jednostkowych za pomocą `.runsettings` pliku.</span><span class="sxs-lookup"><span data-stu-id="efa93-144">Configure unit tests by using a `.runsettings` file.</span></span>](/visualstudio/test/configure-unit-tests-by-using-a-dot-runsettings-file?view=vs-2019)

`-t|--list-tests`

<span data-ttu-id="efa93-145">Listę wszystkich odnalezionych testów w bieżącym projekcie.</span><span class="sxs-lookup"><span data-stu-id="efa93-145">List all of the discovered tests in the current project.</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="efa93-146">Ustawia poziom szczegółowości polecenia.</span><span class="sxs-lookup"><span data-stu-id="efa93-146">Sets the verbosity level of the command.</span></span> <span data-ttu-id="efa93-147">Dozwolone wartości to `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, i `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="efa93-147">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

`RunSettings arguments`

<span data-ttu-id="efa93-148">Argumenty są przekazywane jako RunSettings konfiguracji testu.</span><span class="sxs-lookup"><span data-stu-id="efa93-148">Arguments passed as RunSettings configurations for the test.</span></span> <span data-ttu-id="efa93-149">Argumenty są określane jako `[name]=[value]` pary po "--" (Uwaga miejsca po —).</span><span class="sxs-lookup"><span data-stu-id="efa93-149">Arguments are specified as `[name]=[value]` pairs after "-- " (note the space after --).</span></span> <span data-ttu-id="efa93-150">Spacja jest używana do oddzielania wielu `[name]=[value]` pary.</span><span class="sxs-lookup"><span data-stu-id="efa93-150">A space is used to separate multiple `[name]=[value]` pairs.</span></span>

<span data-ttu-id="efa93-151">Przykład: `dotnet test -- MSTest.DeploymentEnabled=false MSTest.MapInconclusiveToFailed=True`</span><span class="sxs-lookup"><span data-stu-id="efa93-151">Example: `dotnet test -- MSTest.DeploymentEnabled=false MSTest.MapInconclusiveToFailed=True`</span></span>

<span data-ttu-id="efa93-152">Aby uzyskać więcej informacji na temat RunSettings zobacz [vstest.console.exe: Przekazywanie argumentów RunSettings](https://github.com/Microsoft/vstest-docs/blob/master/docs/RunSettingsArguments.md).</span><span class="sxs-lookup"><span data-stu-id="efa93-152">For more information about RunSettings, see [vstest.console.exe: Passing RunSettings args](https://github.com/Microsoft/vstest-docs/blob/master/docs/RunSettingsArguments.md).</span></span>

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="efa93-153">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="efa93-153">.NET Core 2.0</span></span>](#tab/netcore20)

`-a|--test-adapter-path <PATH_TO_ADAPTER>`

<span data-ttu-id="efa93-154">Używa niestandardowych adapterów testowych z określonej ścieżki w przebiegu testu.</span><span class="sxs-lookup"><span data-stu-id="efa93-154">Use the custom test adapters from the specified path in the test run.</span></span>

`-c|--configuration {Debug|Release}`

<span data-ttu-id="efa93-155">Definiuje konfigurację kompilacji.</span><span class="sxs-lookup"><span data-stu-id="efa93-155">Defines the build configuration.</span></span> <span data-ttu-id="efa93-156">Wartość domyślna to `Debug`, ale konfiguracji projektu można zastąpić to ustawienie SDK domyślne.</span><span class="sxs-lookup"><span data-stu-id="efa93-156">The default value is `Debug`, but your project's configuration could override this default SDK setting.</span></span>

`--collect <DATA_COLLECTOR_FRIENDLY_NAME>`

<span data-ttu-id="efa93-157">Włącza moduł zbierający dane dla przebiegu testu.</span><span class="sxs-lookup"><span data-stu-id="efa93-157">Enables data collector for the test run.</span></span> <span data-ttu-id="efa93-158">Aby uzyskać więcej informacji, zobacz [monitorowanie i analizowanie przebiegu testu](https://aka.ms/vstest-collect).</span><span class="sxs-lookup"><span data-stu-id="efa93-158">For more information, see [Monitor and analyze test run](https://aka.ms/vstest-collect).</span></span>

`-d|--diag <PATH_TO_DIAGNOSTICS_FILE>`

<span data-ttu-id="efa93-159">Włącza tryb diagnostycznych dla testu platformy i zapisu komunikaty diagnostyczne do określonego pliku.</span><span class="sxs-lookup"><span data-stu-id="efa93-159">Enables diagnostic mode for the test platform and write diagnostic messages to the specified file.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="efa93-160">Wyszukuje pliki binarne testu dla określonego [framework](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="efa93-160">Looks for test binaries for a specific [framework](../../standard/frameworks.md).</span></span>

`--filter <EXPRESSION>`

<span data-ttu-id="efa93-161">Filtruje testy w bieżącym projekcie za pomocą podanego wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="efa93-161">Filters out tests in the current project using the given expression.</span></span> <span data-ttu-id="efa93-162">Aby uzyskać więcej informacji, zobacz [szczegóły opcji filtru](#filter-option-details) sekcji.</span><span class="sxs-lookup"><span data-stu-id="efa93-162">For more information, see the [Filter option details](#filter-option-details) section.</span></span> <span data-ttu-id="efa93-163">Aby uzyskać dodatkowe informacje i przykłady dotyczące korzystania z jednostki selektywne testowanie filtrowania, zobacz [uruchamianie selektywnych testów jednostkowych](../testing/selective-unit-tests.md).</span><span class="sxs-lookup"><span data-stu-id="efa93-163">For more information and examples on how to use selective unit test filtering, see [Running selective unit tests](../testing/selective-unit-tests.md).</span></span>

`-h|--help`

<span data-ttu-id="efa93-164">Drukuje krótki pomoc dotyczącą polecenia.</span><span class="sxs-lookup"><span data-stu-id="efa93-164">Prints out a short help for the command.</span></span>

`-l|--logger <LoggerUri/FriendlyName>`

<span data-ttu-id="efa93-165">Określa Rejestrator dla wyników badań.</span><span class="sxs-lookup"><span data-stu-id="efa93-165">Specifies a logger for test results.</span></span>

`--no-build`

<span data-ttu-id="efa93-166">Nie da się skompilować projektu testowego przed jego uruchomieniem.</span><span class="sxs-lookup"><span data-stu-id="efa93-166">Doesn't build the test project before running it.</span></span> <span data-ttu-id="efa93-167">Ustawia ona również niejawne `--no-restore` flagi.</span><span class="sxs-lookup"><span data-stu-id="efa93-167">It also implicit sets the `--no-restore` flag.</span></span>

`--no-restore`

<span data-ttu-id="efa93-168">Przy uruchamianiu polecenia niejawne przywracania nie jest wykonywany.</span><span class="sxs-lookup"><span data-stu-id="efa93-168">Doesn't execute an implicit restore when running the command.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="efa93-169">Katalog, w którym można znaleźć plików binarnych do uruchomienia.</span><span class="sxs-lookup"><span data-stu-id="efa93-169">Directory in which to find the binaries to run.</span></span>

`-r|--results-directory <PATH>`

<span data-ttu-id="efa93-170">Katalog, gdzie wyników testu do umieszczenia.</span><span class="sxs-lookup"><span data-stu-id="efa93-170">The directory where the test results are going to be placed.</span></span> <span data-ttu-id="efa93-171">Jeśli określony katalog nie istnieje, zostanie utworzony.</span><span class="sxs-lookup"><span data-stu-id="efa93-171">If the specified directory doesn't exist, it's created.</span></span>

`-s|--settings <SETTINGS_FILE>`

<span data-ttu-id="efa93-172">`.runsettings` Plik używany do uruchamiania testów.</span><span class="sxs-lookup"><span data-stu-id="efa93-172">The `.runsettings` file to use for running the tests.</span></span> [<span data-ttu-id="efa93-173">Konfigurowanie testów jednostkowych za pomocą `.runsettings` pliku.</span><span class="sxs-lookup"><span data-stu-id="efa93-173">Configure unit tests by using a `.runsettings` file.</span></span>](/visualstudio/test/configure-unit-tests-by-using-a-dot-runsettings-file?view=vs-2019)

`-t|--list-tests`

<span data-ttu-id="efa93-174">Listę wszystkich odnalezionych testów w bieżącym projekcie.</span><span class="sxs-lookup"><span data-stu-id="efa93-174">List all of the discovered tests in the current project.</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="efa93-175">Ustawia poziom szczegółowości polecenia.</span><span class="sxs-lookup"><span data-stu-id="efa93-175">Sets the verbosity level of the command.</span></span> <span data-ttu-id="efa93-176">Dozwolone wartości to `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, i `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="efa93-176">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="efa93-177">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="efa93-177">.NET Core 1.x</span></span>](#tab/netcore1x)

`-a|--test-adapter-path <PATH_TO_ADAPTER>`

<span data-ttu-id="efa93-178">Używa niestandardowych adapterów testowych z określonej ścieżki w przebiegu testu.</span><span class="sxs-lookup"><span data-stu-id="efa93-178">Use the custom test adapters from the specified path in the test run.</span></span>

`-c|--configuration {Debug|Release}`

<span data-ttu-id="efa93-179">Definiuje konfigurację kompilacji.</span><span class="sxs-lookup"><span data-stu-id="efa93-179">Defines the build configuration.</span></span> <span data-ttu-id="efa93-180">Wartość domyślna to `Debug`, ale konfiguracji projektu można zastąpić to ustawienie SDK domyślne.</span><span class="sxs-lookup"><span data-stu-id="efa93-180">The default value is `Debug`, but your project's configuration could override this default SDK setting.</span></span>

`-d|--diag <PATH_TO_DIAGNOSTICS_FILE>`

<span data-ttu-id="efa93-181">Włącza tryb diagnostycznych dla testu platformy i zapisu komunikaty diagnostyczne do określonego pliku.</span><span class="sxs-lookup"><span data-stu-id="efa93-181">Enables diagnostic mode for the test platform and write diagnostic messages to the specified file.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="efa93-182">Wyszukuje pliki binarne testu dla określonego [framework](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="efa93-182">Looks for test binaries for a specific [framework](../../standard/frameworks.md).</span></span>

`--filter <EXPRESSION>`

<span data-ttu-id="efa93-183">Filtruje testy w bieżącym projekcie za pomocą podanego wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="efa93-183">Filters out tests in the current project using the given expression.</span></span> <span data-ttu-id="efa93-184">Aby uzyskać więcej informacji, zobacz [szczegóły opcji filtru](#filter-option-details) sekcji.</span><span class="sxs-lookup"><span data-stu-id="efa93-184">For more information, see the [Filter option details](#filter-option-details) section.</span></span> <span data-ttu-id="efa93-185">Aby uzyskać dodatkowe informacje i przykłady dotyczące korzystania z jednostki selektywne testowanie filtrowania, zobacz [uruchamianie selektywnych testów jednostkowych](../testing/selective-unit-tests.md).</span><span class="sxs-lookup"><span data-stu-id="efa93-185">For more information and examples on how to use selective unit test filtering, see [Running selective unit tests](../testing/selective-unit-tests.md).</span></span>

`-h|--help`

<span data-ttu-id="efa93-186">Drukuje krótki pomoc dotyczącą polecenia.</span><span class="sxs-lookup"><span data-stu-id="efa93-186">Prints out a short help for the command.</span></span>

`-l|--logger <LoggerUri/FriendlyName>`

<span data-ttu-id="efa93-187">Określa Rejestrator dla wyników badań.</span><span class="sxs-lookup"><span data-stu-id="efa93-187">Specifies a logger for test results.</span></span>

`--no-build`

<span data-ttu-id="efa93-188">Nie da się skompilować projektu testowego przed jego uruchomieniem.</span><span class="sxs-lookup"><span data-stu-id="efa93-188">Doesn't build the test project before running it.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="efa93-189">Katalog, w którym można znaleźć plików binarnych do uruchomienia.</span><span class="sxs-lookup"><span data-stu-id="efa93-189">Directory in which to find the binaries to run.</span></span>

`-s|--settings <SETTINGS_FILE>`

<span data-ttu-id="efa93-190">`.runsettings` Plik używany do uruchamiania testów.</span><span class="sxs-lookup"><span data-stu-id="efa93-190">The `.runsettings` file to use for running the tests.</span></span> [<span data-ttu-id="efa93-191">Konfigurowanie testów jednostkowych za pomocą `.runsettings` pliku.</span><span class="sxs-lookup"><span data-stu-id="efa93-191">Configure unit tests by using a `.runsettings` file.</span></span>](/visualstudio/test/configure-unit-tests-by-using-a-dot-runsettings-file?view=vs-2019)

`-t|--list-tests`

<span data-ttu-id="efa93-192">Listę wszystkich odnalezionych testów w bieżącym projekcie.</span><span class="sxs-lookup"><span data-stu-id="efa93-192">List all of the discovered tests in the current project.</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="efa93-193">Ustawia poziom szczegółowości polecenia.</span><span class="sxs-lookup"><span data-stu-id="efa93-193">Sets the verbosity level of the command.</span></span> <span data-ttu-id="efa93-194">Dozwolone wartości to `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, i `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="efa93-194">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

---

## <a name="examples"></a><span data-ttu-id="efa93-195">Przykłady</span><span class="sxs-lookup"><span data-stu-id="efa93-195">Examples</span></span>

<span data-ttu-id="efa93-196">Uruchom testy w projekcie w bieżącym katalogu:</span><span class="sxs-lookup"><span data-stu-id="efa93-196">Run the tests in the project in the current directory:</span></span>

`dotnet test`

<span data-ttu-id="efa93-197">Uruchom testy `test1` projektu:</span><span class="sxs-lookup"><span data-stu-id="efa93-197">Run the tests in the `test1` project:</span></span>

`dotnet test ~/projects/test1/test1.csproj`

<span data-ttu-id="efa93-198">Uruchom testy w projekcie w bieżącym katalogu i wygenerować plik wyników testu w formacie trx:</span><span class="sxs-lookup"><span data-stu-id="efa93-198">Run the tests in the project in the current directory and generate a test results file in the trx format:</span></span>

`dotnet test --logger:trx`

## <a name="filter-option-details"></a><span data-ttu-id="efa93-199">Szczegóły opcji filtru</span><span class="sxs-lookup"><span data-stu-id="efa93-199">Filter option details</span></span>

`--filter <EXPRESSION>`

<span data-ttu-id="efa93-200">`<Expression>` ma format `<property><operator><value>[|&<Expression>]`.</span><span class="sxs-lookup"><span data-stu-id="efa93-200">`<Expression>` has the format `<property><operator><value>[|&<Expression>]`.</span></span>

<span data-ttu-id="efa93-201">`<property>` jest to atrybut `Test Case`.</span><span class="sxs-lookup"><span data-stu-id="efa93-201">`<property>` is an attribute of the `Test Case`.</span></span> <span data-ttu-id="efa93-202">Poniżej przedstawiono właściwości obsługiwanych przez platform testów jednostkowych innych popularnych:</span><span class="sxs-lookup"><span data-stu-id="efa93-202">The following are the properties supported by popular unit test frameworks:</span></span>

| <span data-ttu-id="efa93-203">Struktury testowej</span><span class="sxs-lookup"><span data-stu-id="efa93-203">Test Framework</span></span> | <span data-ttu-id="efa93-204">Obsługiwanych właściwości</span><span class="sxs-lookup"><span data-stu-id="efa93-204">Supported properties</span></span>                                                                                      |
| -------------- | --------------------------------------------------------------------------------------------------------- |
| <span data-ttu-id="efa93-205">MSTest</span><span class="sxs-lookup"><span data-stu-id="efa93-205">MSTest</span></span>         | <ul><li><span data-ttu-id="efa93-206">FullyQualifiedName</span><span class="sxs-lookup"><span data-stu-id="efa93-206">FullyQualifiedName</span></span></li><li><span data-ttu-id="efa93-207">Nazwa</span><span class="sxs-lookup"><span data-stu-id="efa93-207">Name</span></span></li><li><span data-ttu-id="efa93-208">ClassName</span><span class="sxs-lookup"><span data-stu-id="efa93-208">ClassName</span></span></li><li><span data-ttu-id="efa93-209">Priorytet</span><span class="sxs-lookup"><span data-stu-id="efa93-209">Priority</span></span></li><li><span data-ttu-id="efa93-210">TestCategory</span><span class="sxs-lookup"><span data-stu-id="efa93-210">TestCategory</span></span></li></ul> |
| <span data-ttu-id="efa93-211">xUnit</span><span class="sxs-lookup"><span data-stu-id="efa93-211">xUnit</span></span>          | <ul><li><span data-ttu-id="efa93-212">FullyQualifiedName</span><span class="sxs-lookup"><span data-stu-id="efa93-212">FullyQualifiedName</span></span></li><li><span data-ttu-id="efa93-213">Nazwa wyświetlana</span><span class="sxs-lookup"><span data-stu-id="efa93-213">DisplayName</span></span></li><li><span data-ttu-id="efa93-214">Cechy</span><span class="sxs-lookup"><span data-stu-id="efa93-214">Traits</span></span></li></ul>                                   |

<span data-ttu-id="efa93-215">`<operator>` Opisuje relację między właściwości i wartości:</span><span class="sxs-lookup"><span data-stu-id="efa93-215">The `<operator>` describes the relationship between the property and the value:</span></span>

| <span data-ttu-id="efa93-216">Operator</span><span class="sxs-lookup"><span data-stu-id="efa93-216">Operator</span></span> | <span data-ttu-id="efa93-217">Funkcja</span><span class="sxs-lookup"><span data-stu-id="efa93-217">Function</span></span>        |
| :------: | --------------- |
| `=`      | <span data-ttu-id="efa93-218">Dokładne dopasowanie</span><span class="sxs-lookup"><span data-stu-id="efa93-218">Exact match</span></span>     |
| `!=`     | <span data-ttu-id="efa93-219">Nie dokładne dopasowanie</span><span class="sxs-lookup"><span data-stu-id="efa93-219">Not exact match</span></span> |
| `~`      | <span data-ttu-id="efa93-220">Zawiera</span><span class="sxs-lookup"><span data-stu-id="efa93-220">Contains</span></span>        |

<span data-ttu-id="efa93-221">`<value>` jest to ciąg.</span><span class="sxs-lookup"><span data-stu-id="efa93-221">`<value>` is a string.</span></span> <span data-ttu-id="efa93-222">Wszystkie wyszukiwania jest rozróżniana wielkość liter.</span><span class="sxs-lookup"><span data-stu-id="efa93-222">All the lookups are case insensitive.</span></span>

<span data-ttu-id="efa93-223">Wyrażenie bez `<operator>` jest automatycznie traktowane jako `contains` na `FullyQualifiedName` właściwości (na przykład `dotnet test --filter xyz` jest taka sama jak `dotnet test --filter FullyQualifiedName~xyz`).</span><span class="sxs-lookup"><span data-stu-id="efa93-223">An expression without an `<operator>` is automatically considered as a `contains` on `FullyQualifiedName` property (for example, `dotnet test --filter xyz` is same as `dotnet test --filter FullyQualifiedName~xyz`).</span></span>

<span data-ttu-id="efa93-224">Wyrażenia może być łączone z operatorów warunkowych:</span><span class="sxs-lookup"><span data-stu-id="efa93-224">Expressions can be joined with conditional operators:</span></span>

| <span data-ttu-id="efa93-225">Operator</span><span class="sxs-lookup"><span data-stu-id="efa93-225">Operator</span></span>            | <span data-ttu-id="efa93-226">Funkcja</span><span class="sxs-lookup"><span data-stu-id="efa93-226">Function</span></span> |
| ------------------- | -------- |
| <code>&#124;</code> | <span data-ttu-id="efa93-227">LUB</span><span class="sxs-lookup"><span data-stu-id="efa93-227">OR</span></span>       |
| `&`                 | <span data-ttu-id="efa93-228">AND</span><span class="sxs-lookup"><span data-stu-id="efa93-228">AND</span></span>      |

<span data-ttu-id="efa93-229">Może być częścią wyrażenia w nawiasach przy użyciu operatorów warunkowych (na przykład `(Name~TestMethod1) | (Name~TestMethod2)`).</span><span class="sxs-lookup"><span data-stu-id="efa93-229">You can enclose expressions in parenthesis when using conditional operators (for example, `(Name~TestMethod1) | (Name~TestMethod2)`).</span></span>

<span data-ttu-id="efa93-230">Aby uzyskać dodatkowe informacje i przykłady dotyczące korzystania z jednostki selektywne testowanie filtrowania, zobacz [uruchamianie selektywnych testów jednostkowych](../testing/selective-unit-tests.md).</span><span class="sxs-lookup"><span data-stu-id="efa93-230">For more information and examples on how to use selective unit test filtering, see [Running selective unit tests](../testing/selective-unit-tests.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="efa93-231">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="efa93-231">See also</span></span>

- [<span data-ttu-id="efa93-232">Struktury i obiekty docelowe</span><span class="sxs-lookup"><span data-stu-id="efa93-232">Frameworks and Targets</span></span>](../../standard/frameworks.md)
- [<span data-ttu-id="efa93-233">Katalog platformy .NET core środowiska uruchomieniowego identyfikator (RID)</span><span class="sxs-lookup"><span data-stu-id="efa93-233">.NET Core Runtime IDentifier (RID) catalog</span></span>](../rid-catalog.md)
