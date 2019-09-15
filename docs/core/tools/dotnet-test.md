---
title: polecenie testu dotnet
description: Polecenie Test dotnet służy do wykonywania testów jednostkowych w danym projekcie.
ms.date: 05/29/2018
ms.openlocfilehash: 49926b35b418e93237a159758903c535ec6c4006
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/14/2019
ms.locfileid: "70988544"
---
# <a name="dotnet-test"></a><span data-ttu-id="fec37-103">dotnet test</span><span class="sxs-lookup"><span data-stu-id="fec37-103">dotnet test</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="fec37-104">Nazwa</span><span class="sxs-lookup"><span data-stu-id="fec37-104">Name</span></span>

<span data-ttu-id="fec37-105">`dotnet test`— Sterownik testowy .NET używany do wykonywania testów jednostkowych.</span><span class="sxs-lookup"><span data-stu-id="fec37-105">`dotnet test` - .NET test driver used to execute unit tests.</span></span>

## <a name="synopsis"></a><span data-ttu-id="fec37-106">Streszczenie</span><span class="sxs-lookup"><span data-stu-id="fec37-106">Synopsis</span></span>

<!-- markdownlint-disable MD025 -->

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="fec37-107">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="fec37-107">.NET Core 2.1</span></span>](#tab/netcore21)

```console
dotnet test [<PROJECT>] [-a|--test-adapter-path] [--blame] [-c|--configuration] [--collect] [-d|--diag] [-f|--framework] [--filter]
    [-l|--logger] [--no-build] [--no-restore] [-o|--output] [-r|--results-directory] [-s|--settings] [-t|--list-tests] 
    [-v|--verbosity] [-- <RunSettings arguments>]

dotnet test [-h|--help]
```

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="fec37-108">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="fec37-108">.NET Core 2.0</span></span>](#tab/netcore20)

```console
dotnet test [<PROJECT>] [-a|--test-adapter-path] [-c|--configuration] [--collect] [-d|--diag] [-f|--framework] [--filter]
    [-l|--logger] [--no-build] [--no-restore] [-o|--output] [-r|--results-directory] [-s|--settings] [-t|--list-tests] [-v|--verbosity]

dotnet test [-h|--help]
```

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="fec37-109">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="fec37-109">.NET Core 1.x</span></span>](#tab/netcore1x)

```console
dotnet test [<PROJECT>] [-a|--test-adapter-path] [-c|--configuration] [-d|--diag] [-f|--framework] [--filter] [-l|--logger] [--no-build] [-o|--output] [-s|--settings] [-t|--list-tests]  [-v|--verbosity]

dotnet test [-h|--help]
```

---

## <a name="description"></a><span data-ttu-id="fec37-110">Opis</span><span class="sxs-lookup"><span data-stu-id="fec37-110">Description</span></span>

<span data-ttu-id="fec37-111">`dotnet test` Polecenie służy do wykonywania testów jednostkowych w danym projekcie.</span><span class="sxs-lookup"><span data-stu-id="fec37-111">The `dotnet test` command is used to execute unit tests in a given project.</span></span> <span data-ttu-id="fec37-112">`dotnet test` Polecenie uruchamia aplikację konsolową Test Runner określoną dla projektu.</span><span class="sxs-lookup"><span data-stu-id="fec37-112">The `dotnet test` command launches the test runner console application specified for a project.</span></span> <span data-ttu-id="fec37-113">Moduł uruchamiający testy wykonuje testy zdefiniowane dla struktury testów jednostkowych (na przykład MSTest, NUnit lub xUnit) i raportuje sukces lub niepowodzenie każdego testu.</span><span class="sxs-lookup"><span data-stu-id="fec37-113">The test runner executes the tests defined for a unit test framework (for example, MSTest, NUnit, or xUnit) and reports the success or failure of each test.</span></span> <span data-ttu-id="fec37-114">Jeśli wszystkie testy zakończą się pomyślnie, moduł uruchamiający testy zwraca 0 jako kod zakończenia; w przeciwnym razie, jeśli dowolny test zakończy się niepowodzeniem, zwraca 1.</span><span class="sxs-lookup"><span data-stu-id="fec37-114">If all tests are successful, the test runner returns 0 as an exit code; otherwise if any test fails, it returns 1.</span></span> <span data-ttu-id="fec37-115">Moduł uruchamiający testy i Biblioteka testów jednostkowych są spakowane jako pakiety NuGet i są przywracane jako zwykłe zależności projektu.</span><span class="sxs-lookup"><span data-stu-id="fec37-115">The test runner and the unit test library are packaged as NuGet packages and are restored as ordinary dependencies for the project.</span></span>

<span data-ttu-id="fec37-116">Projekty testowe określają Test Runner przy użyciu zwykłego `<PackageReference>` elementu, jak pokazano w poniższym przykładowym pliku projektu:</span><span class="sxs-lookup"><span data-stu-id="fec37-116">Test projects specify the test runner using an ordinary `<PackageReference>` element, as seen in the following sample project file:</span></span>

[!code-xml[XUnit Basic Template](../../../samples/snippets/csharp/xunit-test/xunit-test.csproj)]

## <a name="arguments"></a><span data-ttu-id="fec37-117">Argumenty</span><span class="sxs-lookup"><span data-stu-id="fec37-117">Arguments</span></span>

`PROJECT`

<span data-ttu-id="fec37-118">Ścieżka do projektu testowego.</span><span class="sxs-lookup"><span data-stu-id="fec37-118">Path to the test project.</span></span> <span data-ttu-id="fec37-119">Jeśli nie zostanie określony, domyślnie jest bieżącym katalogiem.</span><span class="sxs-lookup"><span data-stu-id="fec37-119">If not specified, it defaults to current directory.</span></span>

## <a name="options"></a><span data-ttu-id="fec37-120">Opcje</span><span class="sxs-lookup"><span data-stu-id="fec37-120">Options</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="fec37-121">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="fec37-121">.NET Core 2.1</span></span>](#tab/netcore21)

`-a|--test-adapter-path <PATH_TO_ADAPTER>`

<span data-ttu-id="fec37-122">Użyj niestandardowych adapterów testowych z określonej ścieżki w przebiegu testu.</span><span class="sxs-lookup"><span data-stu-id="fec37-122">Use the custom test adapters from the specified path in the test run.</span></span>

`--blame`

<span data-ttu-id="fec37-123">Uruchamia testy w trybie polecenia Blame.</span><span class="sxs-lookup"><span data-stu-id="fec37-123">Runs the tests in blame mode.</span></span> <span data-ttu-id="fec37-124">Ta opcja jest pomocna w odizolowaniu problematycznych testów powodujących awarię hosta testowego.</span><span class="sxs-lookup"><span data-stu-id="fec37-124">This option is helpful in isolating the problematic tests causing test host to crash.</span></span> <span data-ttu-id="fec37-125">Tworzy plik wyjściowy w bieżącym katalogu jako *Sequence. XML* , który przechwytuje kolejność testów przed awarią.</span><span class="sxs-lookup"><span data-stu-id="fec37-125">It creates an output file in the current directory as *Sequence.xml* that captures the order of tests execution before the crash.</span></span>

`-c|--configuration {Debug|Release}`

<span data-ttu-id="fec37-126">Definiuje konfigurację kompilacji.</span><span class="sxs-lookup"><span data-stu-id="fec37-126">Defines the build configuration.</span></span> <span data-ttu-id="fec37-127">Wartość domyślna to `Debug`, ale Konfiguracja projektu może zastąpić to domyślne ustawienie zestawu SDK.</span><span class="sxs-lookup"><span data-stu-id="fec37-127">The default value is `Debug`, but your project's configuration could override this default SDK setting.</span></span>

`--collect <DATA_COLLECTOR_FRIENDLY_NAME>`

<span data-ttu-id="fec37-128">Włącza moduł zbierający dane dla przebiegu testu.</span><span class="sxs-lookup"><span data-stu-id="fec37-128">Enables data collector for the test run.</span></span> <span data-ttu-id="fec37-129">Aby uzyskać więcej informacji, zobacz [monitorowanie i analizowanie przebiegu testowego](https://aka.ms/vstest-collect).</span><span class="sxs-lookup"><span data-stu-id="fec37-129">For more information, see [Monitor and analyze test run](https://aka.ms/vstest-collect).</span></span>

`-d|--diag <PATH_TO_DIAGNOSTICS_FILE>`

<span data-ttu-id="fec37-130">Włącza tryb diagnostyczny dla platformy testowej i zapisuje komunikaty diagnostyczne do określonego pliku.</span><span class="sxs-lookup"><span data-stu-id="fec37-130">Enables diagnostic mode for the test platform and write diagnostic messages to the specified file.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="fec37-131">Wyszukuje pliki binarne testów dla konkretnej [struktury](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="fec37-131">Looks for test binaries for a specific [framework](../../standard/frameworks.md).</span></span>

`--filter <EXPRESSION>`

<span data-ttu-id="fec37-132">Filtruje testy w bieżącym projekcie przy użyciu danego wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="fec37-132">Filters out tests in the current project using the given expression.</span></span> <span data-ttu-id="fec37-133">Aby uzyskać więcej informacji, zobacz sekcję [szczegóły opcji filtrowania](#filter-option-details) .</span><span class="sxs-lookup"><span data-stu-id="fec37-133">For more information, see the [Filter option details](#filter-option-details) section.</span></span> <span data-ttu-id="fec37-134">Aby uzyskać więcej informacji i zapoznać się z przykładami dotyczącymi używania selektywnego filtrowania testów jednostkowych, zobacz [Uruchamianie selektywnych testów jednostkowych](../testing/selective-unit-tests.md).</span><span class="sxs-lookup"><span data-stu-id="fec37-134">For more information and examples on how to use selective unit test filtering, see [Running selective unit tests](../testing/selective-unit-tests.md).</span></span>

`-h|--help`

<span data-ttu-id="fec37-135">Drukuje krótką pomoc dla polecenia.</span><span class="sxs-lookup"><span data-stu-id="fec37-135">Prints out a short help for the command.</span></span>

`-l|--logger <LoggerUri/FriendlyName>`

<span data-ttu-id="fec37-136">Określa Rejestrator dla wyników testu.</span><span class="sxs-lookup"><span data-stu-id="fec37-136">Specifies a logger for test results.</span></span>

`--no-build`

<span data-ttu-id="fec37-137">Nie kompiluje projektu testowego przed jego uruchomieniem.</span><span class="sxs-lookup"><span data-stu-id="fec37-137">Doesn't build the test project before running it.</span></span> <span data-ttu-id="fec37-138">Również niejawne ustawia `--no-restore` flagę.</span><span class="sxs-lookup"><span data-stu-id="fec37-138">It also implicit sets the `--no-restore` flag.</span></span>

`--no-restore`

<span data-ttu-id="fec37-139">Nie wykonuje przywracania niejawnego podczas wykonywania polecenia.</span><span class="sxs-lookup"><span data-stu-id="fec37-139">Doesn't execute an implicit restore when running the command.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="fec37-140">Katalog, w którym można znaleźć pliki binarne do uruchomienia.</span><span class="sxs-lookup"><span data-stu-id="fec37-140">Directory in which to find the binaries to run.</span></span>

`-r|--results-directory <PATH>`

<span data-ttu-id="fec37-141">Katalog, w którym zostaną umieszczone wyniki testu.</span><span class="sxs-lookup"><span data-stu-id="fec37-141">The directory where the test results are going to be placed.</span></span> <span data-ttu-id="fec37-142">Jeśli określony katalog nie istnieje, zostanie utworzony.</span><span class="sxs-lookup"><span data-stu-id="fec37-142">If the specified directory doesn't exist, it's created.</span></span>

`-s|--settings <SETTINGS_FILE>`

<span data-ttu-id="fec37-143">Plik `.runsettings` , który ma być używany do uruchamiania testów.</span><span class="sxs-lookup"><span data-stu-id="fec37-143">The `.runsettings` file to use for running the tests.</span></span> [<span data-ttu-id="fec37-144">Skonfiguruj testy jednostkowe przy użyciu `.runsettings` pliku.</span><span class="sxs-lookup"><span data-stu-id="fec37-144">Configure unit tests by using a `.runsettings` file.</span></span>](/visualstudio/test/configure-unit-tests-by-using-a-dot-runsettings-file?view=vs-2019)

`-t|--list-tests`

<span data-ttu-id="fec37-145">Wyświetl listę wszystkich odnalezionych testów w bieżącym projekcie.</span><span class="sxs-lookup"><span data-stu-id="fec37-145">List all of the discovered tests in the current project.</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="fec37-146">Ustawia poziom szczegółowości polecenia.</span><span class="sxs-lookup"><span data-stu-id="fec37-146">Sets the verbosity level of the command.</span></span> <span data-ttu-id="fec37-147">Dozwolone wartości to `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`i .`diag[nostic]`</span><span class="sxs-lookup"><span data-stu-id="fec37-147">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

`RunSettings arguments`

<span data-ttu-id="fec37-148">Argumenty przekazane jako konfiguracje RunSettings dla testu.</span><span class="sxs-lookup"><span data-stu-id="fec37-148">Arguments passed as RunSettings configurations for the test.</span></span> <span data-ttu-id="fec37-149">Argumenty są określane jako `[name]=[value]` pary po "--" (należy zwrócić uwagę na spację po--).</span><span class="sxs-lookup"><span data-stu-id="fec37-149">Arguments are specified as `[name]=[value]` pairs after "-- " (note the space after --).</span></span> <span data-ttu-id="fec37-150">Spacja jest używana do rozdzielania wielu `[name]=[value]` par.</span><span class="sxs-lookup"><span data-stu-id="fec37-150">A space is used to separate multiple `[name]=[value]` pairs.</span></span>

<span data-ttu-id="fec37-151">Przykład: `dotnet test -- MSTest.DeploymentEnabled=false MSTest.MapInconclusiveToFailed=True`</span><span class="sxs-lookup"><span data-stu-id="fec37-151">Example: `dotnet test -- MSTest.DeploymentEnabled=false MSTest.MapInconclusiveToFailed=True`</span></span>

<span data-ttu-id="fec37-152">Aby uzyskać więcej informacji na temat runsettings [, zobacz VSTest. Console. exe: Przekazywanie argumentów](https://github.com/Microsoft/vstest-docs/blob/master/docs/RunSettingsArguments.md)runsettings.</span><span class="sxs-lookup"><span data-stu-id="fec37-152">For more information about RunSettings, see [vstest.console.exe: Passing RunSettings args](https://github.com/Microsoft/vstest-docs/blob/master/docs/RunSettingsArguments.md).</span></span>

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="fec37-153">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="fec37-153">.NET Core 2.0</span></span>](#tab/netcore20)

`-a|--test-adapter-path <PATH_TO_ADAPTER>`

<span data-ttu-id="fec37-154">Użyj niestandardowych adapterów testowych z określonej ścieżki w przebiegu testu.</span><span class="sxs-lookup"><span data-stu-id="fec37-154">Use the custom test adapters from the specified path in the test run.</span></span>

`-c|--configuration {Debug|Release}`

<span data-ttu-id="fec37-155">Definiuje konfigurację kompilacji.</span><span class="sxs-lookup"><span data-stu-id="fec37-155">Defines the build configuration.</span></span> <span data-ttu-id="fec37-156">Wartość domyślna to `Debug`, ale Konfiguracja projektu może zastąpić to domyślne ustawienie zestawu SDK.</span><span class="sxs-lookup"><span data-stu-id="fec37-156">The default value is `Debug`, but your project's configuration could override this default SDK setting.</span></span>

`--collect <DATA_COLLECTOR_FRIENDLY_NAME>`

<span data-ttu-id="fec37-157">Włącza moduł zbierający dane dla przebiegu testu.</span><span class="sxs-lookup"><span data-stu-id="fec37-157">Enables data collector for the test run.</span></span> <span data-ttu-id="fec37-158">Aby uzyskać więcej informacji, zobacz [monitorowanie i analizowanie przebiegu testowego](https://aka.ms/vstest-collect).</span><span class="sxs-lookup"><span data-stu-id="fec37-158">For more information, see [Monitor and analyze test run](https://aka.ms/vstest-collect).</span></span>

`-d|--diag <PATH_TO_DIAGNOSTICS_FILE>`

<span data-ttu-id="fec37-159">Włącza tryb diagnostyczny dla platformy testowej i zapisuje komunikaty diagnostyczne do określonego pliku.</span><span class="sxs-lookup"><span data-stu-id="fec37-159">Enables diagnostic mode for the test platform and write diagnostic messages to the specified file.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="fec37-160">Wyszukuje pliki binarne testów dla konkretnej [struktury](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="fec37-160">Looks for test binaries for a specific [framework](../../standard/frameworks.md).</span></span>

`--filter <EXPRESSION>`

<span data-ttu-id="fec37-161">Filtruje testy w bieżącym projekcie przy użyciu danego wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="fec37-161">Filters out tests in the current project using the given expression.</span></span> <span data-ttu-id="fec37-162">Aby uzyskać więcej informacji, zobacz sekcję [szczegóły opcji filtrowania](#filter-option-details) .</span><span class="sxs-lookup"><span data-stu-id="fec37-162">For more information, see the [Filter option details](#filter-option-details) section.</span></span> <span data-ttu-id="fec37-163">Aby uzyskać więcej informacji i zapoznać się z przykładami dotyczącymi używania selektywnego filtrowania testów jednostkowych, zobacz [Uruchamianie selektywnych testów jednostkowych](../testing/selective-unit-tests.md).</span><span class="sxs-lookup"><span data-stu-id="fec37-163">For more information and examples on how to use selective unit test filtering, see [Running selective unit tests](../testing/selective-unit-tests.md).</span></span>

`-h|--help`

<span data-ttu-id="fec37-164">Drukuje krótką pomoc dla polecenia.</span><span class="sxs-lookup"><span data-stu-id="fec37-164">Prints out a short help for the command.</span></span>

`-l|--logger <LoggerUri/FriendlyName>`

<span data-ttu-id="fec37-165">Określa Rejestrator dla wyników testu.</span><span class="sxs-lookup"><span data-stu-id="fec37-165">Specifies a logger for test results.</span></span>

`--no-build`

<span data-ttu-id="fec37-166">Nie kompiluje projektu testowego przed jego uruchomieniem.</span><span class="sxs-lookup"><span data-stu-id="fec37-166">Doesn't build the test project before running it.</span></span> <span data-ttu-id="fec37-167">Również niejawne ustawia `--no-restore` flagę.</span><span class="sxs-lookup"><span data-stu-id="fec37-167">It also implicit sets the `--no-restore` flag.</span></span>

`--no-restore`

<span data-ttu-id="fec37-168">Nie wykonuje przywracania niejawnego podczas wykonywania polecenia.</span><span class="sxs-lookup"><span data-stu-id="fec37-168">Doesn't execute an implicit restore when running the command.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="fec37-169">Katalog, w którym można znaleźć pliki binarne do uruchomienia.</span><span class="sxs-lookup"><span data-stu-id="fec37-169">Directory in which to find the binaries to run.</span></span>

`-r|--results-directory <PATH>`

<span data-ttu-id="fec37-170">Katalog, w którym zostaną umieszczone wyniki testu.</span><span class="sxs-lookup"><span data-stu-id="fec37-170">The directory where the test results are going to be placed.</span></span> <span data-ttu-id="fec37-171">Jeśli określony katalog nie istnieje, zostanie utworzony.</span><span class="sxs-lookup"><span data-stu-id="fec37-171">If the specified directory doesn't exist, it's created.</span></span>

`-s|--settings <SETTINGS_FILE>`

<span data-ttu-id="fec37-172">Plik `.runsettings` , który ma być używany do uruchamiania testów.</span><span class="sxs-lookup"><span data-stu-id="fec37-172">The `.runsettings` file to use for running the tests.</span></span> [<span data-ttu-id="fec37-173">Skonfiguruj testy jednostkowe przy użyciu `.runsettings` pliku.</span><span class="sxs-lookup"><span data-stu-id="fec37-173">Configure unit tests by using a `.runsettings` file.</span></span>](/visualstudio/test/configure-unit-tests-by-using-a-dot-runsettings-file?view=vs-2019)

`-t|--list-tests`

<span data-ttu-id="fec37-174">Wyświetl listę wszystkich odnalezionych testów w bieżącym projekcie.</span><span class="sxs-lookup"><span data-stu-id="fec37-174">List all of the discovered tests in the current project.</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="fec37-175">Ustawia poziom szczegółowości polecenia.</span><span class="sxs-lookup"><span data-stu-id="fec37-175">Sets the verbosity level of the command.</span></span> <span data-ttu-id="fec37-176">Dozwolone wartości to `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`i .`diag[nostic]`</span><span class="sxs-lookup"><span data-stu-id="fec37-176">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="fec37-177">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="fec37-177">.NET Core 1.x</span></span>](#tab/netcore1x)

`-a|--test-adapter-path <PATH_TO_ADAPTER>`

<span data-ttu-id="fec37-178">Użyj niestandardowych adapterów testowych z określonej ścieżki w przebiegu testu.</span><span class="sxs-lookup"><span data-stu-id="fec37-178">Use the custom test adapters from the specified path in the test run.</span></span>

`-c|--configuration {Debug|Release}`

<span data-ttu-id="fec37-179">Definiuje konfigurację kompilacji.</span><span class="sxs-lookup"><span data-stu-id="fec37-179">Defines the build configuration.</span></span> <span data-ttu-id="fec37-180">Wartość domyślna to `Debug`, ale Konfiguracja projektu może zastąpić to domyślne ustawienie zestawu SDK.</span><span class="sxs-lookup"><span data-stu-id="fec37-180">The default value is `Debug`, but your project's configuration could override this default SDK setting.</span></span>

`-d|--diag <PATH_TO_DIAGNOSTICS_FILE>`

<span data-ttu-id="fec37-181">Włącza tryb diagnostyczny dla platformy testowej i zapisuje komunikaty diagnostyczne do określonego pliku.</span><span class="sxs-lookup"><span data-stu-id="fec37-181">Enables diagnostic mode for the test platform and write diagnostic messages to the specified file.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="fec37-182">Wyszukuje pliki binarne testów dla konkretnej [struktury](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="fec37-182">Looks for test binaries for a specific [framework](../../standard/frameworks.md).</span></span>

`--filter <EXPRESSION>`

<span data-ttu-id="fec37-183">Filtruje testy w bieżącym projekcie przy użyciu danego wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="fec37-183">Filters out tests in the current project using the given expression.</span></span> <span data-ttu-id="fec37-184">Aby uzyskać więcej informacji, zobacz sekcję [szczegóły opcji filtrowania](#filter-option-details) .</span><span class="sxs-lookup"><span data-stu-id="fec37-184">For more information, see the [Filter option details](#filter-option-details) section.</span></span> <span data-ttu-id="fec37-185">Aby uzyskać więcej informacji i zapoznać się z przykładami dotyczącymi używania selektywnego filtrowania testów jednostkowych, zobacz [Uruchamianie selektywnych testów jednostkowych](../testing/selective-unit-tests.md).</span><span class="sxs-lookup"><span data-stu-id="fec37-185">For more information and examples on how to use selective unit test filtering, see [Running selective unit tests](../testing/selective-unit-tests.md).</span></span>

`-h|--help`

<span data-ttu-id="fec37-186">Drukuje krótką pomoc dla polecenia.</span><span class="sxs-lookup"><span data-stu-id="fec37-186">Prints out a short help for the command.</span></span>

`-l|--logger <LoggerUri/FriendlyName>`

<span data-ttu-id="fec37-187">Określa Rejestrator dla wyników testu.</span><span class="sxs-lookup"><span data-stu-id="fec37-187">Specifies a logger for test results.</span></span>

`--no-build`

<span data-ttu-id="fec37-188">Nie kompiluje projektu testowego przed jego uruchomieniem.</span><span class="sxs-lookup"><span data-stu-id="fec37-188">Doesn't build the test project before running it.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="fec37-189">Katalog, w którym można znaleźć pliki binarne do uruchomienia.</span><span class="sxs-lookup"><span data-stu-id="fec37-189">Directory in which to find the binaries to run.</span></span>

`-s|--settings <SETTINGS_FILE>`

<span data-ttu-id="fec37-190">Plik `.runsettings` , który ma być używany do uruchamiania testów.</span><span class="sxs-lookup"><span data-stu-id="fec37-190">The `.runsettings` file to use for running the tests.</span></span> [<span data-ttu-id="fec37-191">Skonfiguruj testy jednostkowe przy użyciu `.runsettings` pliku.</span><span class="sxs-lookup"><span data-stu-id="fec37-191">Configure unit tests by using a `.runsettings` file.</span></span>](/visualstudio/test/configure-unit-tests-by-using-a-dot-runsettings-file?view=vs-2019)

`-t|--list-tests`

<span data-ttu-id="fec37-192">Wyświetl listę wszystkich odnalezionych testów w bieżącym projekcie.</span><span class="sxs-lookup"><span data-stu-id="fec37-192">List all of the discovered tests in the current project.</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="fec37-193">Ustawia poziom szczegółowości polecenia.</span><span class="sxs-lookup"><span data-stu-id="fec37-193">Sets the verbosity level of the command.</span></span> <span data-ttu-id="fec37-194">Dozwolone wartości to `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`i .`diag[nostic]`</span><span class="sxs-lookup"><span data-stu-id="fec37-194">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

---

## <a name="examples"></a><span data-ttu-id="fec37-195">Przykłady</span><span class="sxs-lookup"><span data-stu-id="fec37-195">Examples</span></span>

<span data-ttu-id="fec37-196">Uruchom testy w projekcie w bieżącym katalogu:</span><span class="sxs-lookup"><span data-stu-id="fec37-196">Run the tests in the project in the current directory:</span></span>

`dotnet test`

<span data-ttu-id="fec37-197">Uruchom testy w `test1` projekcie:</span><span class="sxs-lookup"><span data-stu-id="fec37-197">Run the tests in the `test1` project:</span></span>

`dotnet test ~/projects/test1/test1.csproj`

<span data-ttu-id="fec37-198">Uruchom testy w projekcie w bieżącym katalogu i wygeneruj plik wyników testu w formacie TRX:</span><span class="sxs-lookup"><span data-stu-id="fec37-198">Run the tests in the project in the current directory and generate a test results file in the trx format:</span></span>

`dotnet test --logger trx`

## <a name="filter-option-details"></a><span data-ttu-id="fec37-199">Szczegóły opcji filtrowania</span><span class="sxs-lookup"><span data-stu-id="fec37-199">Filter option details</span></span>

`--filter <EXPRESSION>`

<span data-ttu-id="fec37-200">`<Expression>`ma format `<property><operator><value>[|&<Expression>]`.</span><span class="sxs-lookup"><span data-stu-id="fec37-200">`<Expression>` has the format `<property><operator><value>[|&<Expression>]`.</span></span>

<span data-ttu-id="fec37-201">`<property>`jest atrybutem `Test Case`klasy.</span><span class="sxs-lookup"><span data-stu-id="fec37-201">`<property>` is an attribute of the `Test Case`.</span></span> <span data-ttu-id="fec37-202">Poniżej przedstawiono właściwości obsługiwane przez popularne struktury testów jednostkowych:</span><span class="sxs-lookup"><span data-stu-id="fec37-202">The following are the properties supported by popular unit test frameworks:</span></span>

| <span data-ttu-id="fec37-203">Struktury testowej</span><span class="sxs-lookup"><span data-stu-id="fec37-203">Test Framework</span></span> | <span data-ttu-id="fec37-204">Obsługiwane właściwości</span><span class="sxs-lookup"><span data-stu-id="fec37-204">Supported properties</span></span>                                                                                      |
| -------------- | --------------------------------------------------------------------------------------------------------- |
| <span data-ttu-id="fec37-205">MSTest</span><span class="sxs-lookup"><span data-stu-id="fec37-205">MSTest</span></span>         | <ul><li><span data-ttu-id="fec37-206">FullyQualifiedName</span><span class="sxs-lookup"><span data-stu-id="fec37-206">FullyQualifiedName</span></span></li><li><span data-ttu-id="fec37-207">Nazwa</span><span class="sxs-lookup"><span data-stu-id="fec37-207">Name</span></span></li><li><span data-ttu-id="fec37-208">Nazwą</span><span class="sxs-lookup"><span data-stu-id="fec37-208">ClassName</span></span></li><li><span data-ttu-id="fec37-209">Priority</span><span class="sxs-lookup"><span data-stu-id="fec37-209">Priority</span></span></li><li><span data-ttu-id="fec37-210">TestCategory</span><span class="sxs-lookup"><span data-stu-id="fec37-210">TestCategory</span></span></li></ul> |
| <span data-ttu-id="fec37-211">xUnit</span><span class="sxs-lookup"><span data-stu-id="fec37-211">xUnit</span></span>          | <ul><li><span data-ttu-id="fec37-212">FullyQualifiedName</span><span class="sxs-lookup"><span data-stu-id="fec37-212">FullyQualifiedName</span></span></li><li><span data-ttu-id="fec37-213">DisplayName</span><span class="sxs-lookup"><span data-stu-id="fec37-213">DisplayName</span></span></li><li><span data-ttu-id="fec37-214">Cech</span><span class="sxs-lookup"><span data-stu-id="fec37-214">Traits</span></span></li></ul>                                   |

<span data-ttu-id="fec37-215">`<operator>` Opisuje relację między właściwością a wartością:</span><span class="sxs-lookup"><span data-stu-id="fec37-215">The `<operator>` describes the relationship between the property and the value:</span></span>

| <span data-ttu-id="fec37-216">Operator</span><span class="sxs-lookup"><span data-stu-id="fec37-216">Operator</span></span> | <span data-ttu-id="fec37-217">Funkcja</span><span class="sxs-lookup"><span data-stu-id="fec37-217">Function</span></span>        |
| :------: | --------------- |
| `=`      | <span data-ttu-id="fec37-218">Dokładne dopasowanie</span><span class="sxs-lookup"><span data-stu-id="fec37-218">Exact match</span></span>     |
| `!=`     | <span data-ttu-id="fec37-219">Niedokładne dopasowanie</span><span class="sxs-lookup"><span data-stu-id="fec37-219">Not exact match</span></span> |
| `~`      | <span data-ttu-id="fec37-220">Zawiera</span><span class="sxs-lookup"><span data-stu-id="fec37-220">Contains</span></span>        |

<span data-ttu-id="fec37-221">`<value>`jest ciągiem.</span><span class="sxs-lookup"><span data-stu-id="fec37-221">`<value>` is a string.</span></span> <span data-ttu-id="fec37-222">Wszystkie wyszukiwania są rozróżniane wielkości liter.</span><span class="sxs-lookup"><span data-stu-id="fec37-222">All the lookups are case insensitive.</span></span>

<span data-ttu-id="fec37-223">`<operator>` Wyrażenie bez elementu jest automatycznie uznawane `dotnet test --filter xyz` `contains` za Właściwość on `FullyQualifiedName` (na przykład jest takie samo jak `dotnet test --filter FullyQualifiedName~xyz`).</span><span class="sxs-lookup"><span data-stu-id="fec37-223">An expression without an `<operator>` is automatically considered as a `contains` on `FullyQualifiedName` property (for example, `dotnet test --filter xyz` is same as `dotnet test --filter FullyQualifiedName~xyz`).</span></span>

<span data-ttu-id="fec37-224">Wyrażenia mogą być dołączane za pomocą operatorów warunkowych:</span><span class="sxs-lookup"><span data-stu-id="fec37-224">Expressions can be joined with conditional operators:</span></span>

| <span data-ttu-id="fec37-225">Operator</span><span class="sxs-lookup"><span data-stu-id="fec37-225">Operator</span></span>            | <span data-ttu-id="fec37-226">Funkcja</span><span class="sxs-lookup"><span data-stu-id="fec37-226">Function</span></span> |
| ------------------- | -------- |
| <code>&#124;</code> | <span data-ttu-id="fec37-227">LUB</span><span class="sxs-lookup"><span data-stu-id="fec37-227">OR</span></span>       |
| `&`                 | <span data-ttu-id="fec37-228">AND</span><span class="sxs-lookup"><span data-stu-id="fec37-228">AND</span></span>      |

<span data-ttu-id="fec37-229">Wyrażenia można ująć w nawiasy, gdy są używane operatory warunkowe (na przykład `(Name~TestMethod1) | (Name~TestMethod2)`).</span><span class="sxs-lookup"><span data-stu-id="fec37-229">You can enclose expressions in parenthesis when using conditional operators (for example, `(Name~TestMethod1) | (Name~TestMethod2)`).</span></span>

<span data-ttu-id="fec37-230">Aby uzyskać więcej informacji i zapoznać się z przykładami dotyczącymi używania selektywnego filtrowania testów jednostkowych, zobacz [Uruchamianie selektywnych testów jednostkowych](../testing/selective-unit-tests.md).</span><span class="sxs-lookup"><span data-stu-id="fec37-230">For more information and examples on how to use selective unit test filtering, see [Running selective unit tests](../testing/selective-unit-tests.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="fec37-231">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="fec37-231">See also</span></span>

- [<span data-ttu-id="fec37-232">Struktury i elementy docelowe</span><span class="sxs-lookup"><span data-stu-id="fec37-232">Frameworks and Targets</span></span>](../../standard/frameworks.md)
- [<span data-ttu-id="fec37-233">Wykaz identyfikatorów środowiska uruchomieniowego platformy .NET Core (RID)</span><span class="sxs-lookup"><span data-stu-id="fec37-233">.NET Core Runtime IDentifier (RID) catalog</span></span>](../rid-catalog.md)
