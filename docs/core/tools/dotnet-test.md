---
title: polecenie testu dotnet
description: Polecenie Test dotnet służy do wykonywania testów jednostkowych w danym projekcie.
ms.date: 05/29/2018
ms.openlocfilehash: 909815151265117395c6d8d13b4443a245c05f9e
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/19/2020
ms.locfileid: "77451197"
---
# <a name="dotnet-test"></a><span data-ttu-id="1e124-103">dotnet test</span><span class="sxs-lookup"><span data-stu-id="1e124-103">dotnet test</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="1e124-104">Name (Nazwa)</span><span class="sxs-lookup"><span data-stu-id="1e124-104">Name</span></span>

<span data-ttu-id="1e124-105">`dotnet test` — sterownik testowy .NET używany do wykonywania testów jednostkowych.</span><span class="sxs-lookup"><span data-stu-id="1e124-105">`dotnet test` - .NET test driver used to execute unit tests.</span></span>

## <a name="synopsis"></a><span data-ttu-id="1e124-106">Streszczenie</span><span class="sxs-lookup"><span data-stu-id="1e124-106">Synopsis</span></span>

<!-- markdownlint-disable MD025 -->

# <a name="net-core-21"></a>[<span data-ttu-id="1e124-107">.NET Core 2,1</span><span class="sxs-lookup"><span data-stu-id="1e124-107">.NET Core 2.1</span></span>](#tab/netcore21)

```dotnetcli
dotnet test [<PROJECT>] [-a|--test-adapter-path] [--blame] [-c|--configuration] [--collect] [-d|--diag] [-f|--framework] [--filter]
    [-l|--logger] [--no-build] [--no-restore] [-o|--output] [-r|--results-directory] [-s|--settings] [-t|--list-tests] 
    [-v|--verbosity] [-- <RunSettings arguments>]

dotnet test [-h|--help]
```

# <a name="net-core-20"></a>[<span data-ttu-id="1e124-108">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="1e124-108">.NET Core 2.0</span></span>](#tab/netcore20)

```dotnetcli
dotnet test [<PROJECT>] [-a|--test-adapter-path] [-c|--configuration] [--collect] [-d|--diag] [-f|--framework] [--filter]
    [-l|--logger] [--no-build] [--no-restore] [-o|--output] [-r|--results-directory] [-s|--settings] [-t|--list-tests] [-v|--verbosity]

dotnet test [-h|--help]
```

# <a name="net-core-1x"></a>[<span data-ttu-id="1e124-109">.NET Core 1. x</span><span class="sxs-lookup"><span data-stu-id="1e124-109">.NET Core 1.x</span></span>](#tab/netcore1x)

```dotnetcli
dotnet test [<PROJECT>] [-a|--test-adapter-path] [-c|--configuration] [-d|--diag] [-f|--framework] [--filter] [-l|--logger] [--no-build] [-o|--output] [-s|--settings] [-t|--list-tests]  [-v|--verbosity]

dotnet test [-h|--help]
```

---

## <a name="description"></a><span data-ttu-id="1e124-110">Opis</span><span class="sxs-lookup"><span data-stu-id="1e124-110">Description</span></span>

<span data-ttu-id="1e124-111">Polecenie `dotnet test` służy do wykonywania testów jednostkowych w danym projekcie.</span><span class="sxs-lookup"><span data-stu-id="1e124-111">The `dotnet test` command is used to execute unit tests in a given project.</span></span> <span data-ttu-id="1e124-112">`dotnet test` polecenie uruchamia aplikację konsolową Test Runner określoną dla projektu.</span><span class="sxs-lookup"><span data-stu-id="1e124-112">The `dotnet test` command launches the test runner console application specified for a project.</span></span> <span data-ttu-id="1e124-113">Moduł uruchamiający testy wykonuje testy zdefiniowane dla struktury testów jednostkowych (na przykład MSTest, NUnit lub xUnit) i raportuje sukces lub niepowodzenie każdego testu.</span><span class="sxs-lookup"><span data-stu-id="1e124-113">The test runner executes the tests defined for a unit test framework (for example, MSTest, NUnit, or xUnit) and reports the success or failure of each test.</span></span> <span data-ttu-id="1e124-114">Jeśli wszystkie testy zakończą się pomyślnie, moduł uruchamiający testy zwraca 0 jako kod zakończenia; w przeciwnym razie, jeśli dowolny test zakończy się niepowodzeniem, zwraca 1.</span><span class="sxs-lookup"><span data-stu-id="1e124-114">If all tests are successful, the test runner returns 0 as an exit code; otherwise if any test fails, it returns 1.</span></span> <span data-ttu-id="1e124-115">Moduł uruchamiający testy i Biblioteka testów jednostkowych są spakowane jako pakiety NuGet i są przywracane jako zwykłe zależności projektu.</span><span class="sxs-lookup"><span data-stu-id="1e124-115">The test runner and the unit test library are packaged as NuGet packages and are restored as ordinary dependencies for the project.</span></span>

<span data-ttu-id="1e124-116">Projekty testowe określają Test Runner przy użyciu zwykłego elementu `<PackageReference>`, jak pokazano w poniższym przykładowym pliku projektu:</span><span class="sxs-lookup"><span data-stu-id="1e124-116">Test projects specify the test runner using an ordinary `<PackageReference>` element, as seen in the following sample project file:</span></span>

[!code-xml[XUnit Basic Template](../../../samples/snippets/csharp/xunit-test/xunit-test.csproj)]

## <a name="arguments"></a><span data-ttu-id="1e124-117">Argumenty</span><span class="sxs-lookup"><span data-stu-id="1e124-117">Arguments</span></span>

`PROJECT`

<span data-ttu-id="1e124-118">Ścieżka do projektu testowego.</span><span class="sxs-lookup"><span data-stu-id="1e124-118">Path to the test project.</span></span> <span data-ttu-id="1e124-119">Jeśli nie zostanie określony, domyślnie jest bieżącym katalogiem.</span><span class="sxs-lookup"><span data-stu-id="1e124-119">If not specified, it defaults to current directory.</span></span>

## <a name="options"></a><span data-ttu-id="1e124-120">Opcje</span><span class="sxs-lookup"><span data-stu-id="1e124-120">Options</span></span>

# <a name="net-core-21"></a>[<span data-ttu-id="1e124-121">.NET Core 2,1</span><span class="sxs-lookup"><span data-stu-id="1e124-121">.NET Core 2.1</span></span>](#tab/netcore21)

`-a|--test-adapter-path <PATH_TO_ADAPTER>`

<span data-ttu-id="1e124-122">Użyj niestandardowych adapterów testowych z określonej ścieżki w przebiegu testu.</span><span class="sxs-lookup"><span data-stu-id="1e124-122">Use the custom test adapters from the specified path in the test run.</span></span>

`--blame`

<span data-ttu-id="1e124-123">Uruchamia testy w trybie polecenia Blame.</span><span class="sxs-lookup"><span data-stu-id="1e124-123">Runs the tests in blame mode.</span></span> <span data-ttu-id="1e124-124">Ta opcja jest pomocna w odizolowaniu problematycznych testów powodujących awarię hosta testowego.</span><span class="sxs-lookup"><span data-stu-id="1e124-124">This option is helpful in isolating the problematic tests causing test host to crash.</span></span> <span data-ttu-id="1e124-125">Tworzy plik wyjściowy w bieżącym katalogu jako *Sequence. XML* , który przechwytuje kolejność testów przed awarią.</span><span class="sxs-lookup"><span data-stu-id="1e124-125">It creates an output file in the current directory as *Sequence.xml* that captures the order of tests execution before the crash.</span></span>

`-c|--configuration {Debug|Release}`

<span data-ttu-id="1e124-126">Definiuje konfigurację kompilacji.</span><span class="sxs-lookup"><span data-stu-id="1e124-126">Defines the build configuration.</span></span> <span data-ttu-id="1e124-127">Wartość domyślna to `Debug`, ale Konfiguracja projektu może zastąpić to domyślne ustawienie zestawu SDK.</span><span class="sxs-lookup"><span data-stu-id="1e124-127">The default value is `Debug`, but your project's configuration could override this default SDK setting.</span></span>

`--collect <DATA_COLLECTOR_FRIENDLY_NAME>`

<span data-ttu-id="1e124-128">Włącza moduł zbierający dane dla przebiegu testu.</span><span class="sxs-lookup"><span data-stu-id="1e124-128">Enables data collector for the test run.</span></span> <span data-ttu-id="1e124-129">Aby uzyskać więcej informacji, zobacz [monitorowanie i analizowanie przebiegu testowego](https://aka.ms/vstest-collect).</span><span class="sxs-lookup"><span data-stu-id="1e124-129">For more information, see [Monitor and analyze test run](https://aka.ms/vstest-collect).</span></span>

`-d|--diag <PATH_TO_DIAGNOSTICS_FILE>`

<span data-ttu-id="1e124-130">Włącza tryb diagnostyczny dla platformy testowej i zapisuje komunikaty diagnostyczne do określonego pliku.</span><span class="sxs-lookup"><span data-stu-id="1e124-130">Enables diagnostic mode for the test platform and write diagnostic messages to the specified file.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="1e124-131">Wyszukuje pliki binarne testów dla konkretnej [struktury](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="1e124-131">Looks for test binaries for a specific [framework](../../standard/frameworks.md).</span></span>

`--filter <EXPRESSION>`

<span data-ttu-id="1e124-132">Filtruje testy w bieżącym projekcie przy użyciu danego wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="1e124-132">Filters out tests in the current project using the given expression.</span></span> <span data-ttu-id="1e124-133">Aby uzyskać więcej informacji, zobacz sekcję [szczegóły opcji filtrowania](#filter-option-details) .</span><span class="sxs-lookup"><span data-stu-id="1e124-133">For more information, see the [Filter option details](#filter-option-details) section.</span></span> <span data-ttu-id="1e124-134">Aby uzyskać więcej informacji i zapoznać się z przykładami dotyczącymi używania selektywnego filtrowania testów jednostkowych, zobacz [Uruchamianie selektywnych testów jednostkowych](../testing/selective-unit-tests.md).</span><span class="sxs-lookup"><span data-stu-id="1e124-134">For more information and examples on how to use selective unit test filtering, see [Running selective unit tests](../testing/selective-unit-tests.md).</span></span>

`-h|--help`

<span data-ttu-id="1e124-135">Drukuje krótką pomoc dla polecenia.</span><span class="sxs-lookup"><span data-stu-id="1e124-135">Prints out a short help for the command.</span></span>

`-l|--logger <LoggerUri/FriendlyName>`

<span data-ttu-id="1e124-136">Określa Rejestrator dla wyników testu.</span><span class="sxs-lookup"><span data-stu-id="1e124-136">Specifies a logger for test results.</span></span>

`--no-build`

<span data-ttu-id="1e124-137">Nie kompiluje projektu testowego przed jego uruchomieniem.</span><span class="sxs-lookup"><span data-stu-id="1e124-137">Doesn't build the test project before running it.</span></span> <span data-ttu-id="1e124-138">Również niejawne ustawia flagę `--no-restore`.</span><span class="sxs-lookup"><span data-stu-id="1e124-138">It also implicit sets the `--no-restore` flag.</span></span>

`--no-restore`

<span data-ttu-id="1e124-139">Nie wykonuje przywracania niejawnego podczas wykonywania polecenia.</span><span class="sxs-lookup"><span data-stu-id="1e124-139">Doesn't execute an implicit restore when running the command.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="1e124-140">Katalog, w którym można znaleźć pliki binarne do uruchomienia.</span><span class="sxs-lookup"><span data-stu-id="1e124-140">Directory in which to find the binaries to run.</span></span>

`-r|--results-directory <PATH>`

<span data-ttu-id="1e124-141">Katalog, w którym zostaną umieszczone wyniki testu.</span><span class="sxs-lookup"><span data-stu-id="1e124-141">The directory where the test results are going to be placed.</span></span> <span data-ttu-id="1e124-142">Jeśli określony katalog nie istnieje, zostanie utworzony.</span><span class="sxs-lookup"><span data-stu-id="1e124-142">If the specified directory doesn't exist, it's created.</span></span>

`-s|--settings <SETTINGS_FILE>`

<span data-ttu-id="1e124-143">Plik `.runsettings` używany do uruchamiania testów.</span><span class="sxs-lookup"><span data-stu-id="1e124-143">The `.runsettings` file to use for running the tests.</span></span> [<span data-ttu-id="1e124-144">Skonfiguruj testy jednostkowe za pomocą pliku `.runsettings`.</span><span class="sxs-lookup"><span data-stu-id="1e124-144">Configure unit tests by using a `.runsettings` file.</span></span>](/visualstudio/test/configure-unit-tests-by-using-a-dot-runsettings-file)

`-t|--list-tests`

<span data-ttu-id="1e124-145">Wyświetl listę wszystkich odnalezionych testów w bieżącym projekcie.</span><span class="sxs-lookup"><span data-stu-id="1e124-145">List all of the discovered tests in the current project.</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="1e124-146">Ustawia poziom szczegółowości polecenia.</span><span class="sxs-lookup"><span data-stu-id="1e124-146">Sets the verbosity level of the command.</span></span> <span data-ttu-id="1e124-147">Dozwolone wartości to `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`i `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="1e124-147">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

`RunSettings arguments`

<span data-ttu-id="1e124-148">Argumenty przekazane jako konfiguracje RunSettings dla testu.</span><span class="sxs-lookup"><span data-stu-id="1e124-148">Arguments passed as RunSettings configurations for the test.</span></span> <span data-ttu-id="1e124-149">Argumenty są określane jako pary `[name]=[value]` po "--" (należy zwrócić uwagę na spację po--).</span><span class="sxs-lookup"><span data-stu-id="1e124-149">Arguments are specified as `[name]=[value]` pairs after "-- " (note the space after --).</span></span> <span data-ttu-id="1e124-150">Spacja jest używana do rozdzielania wielu par `[name]=[value]`.</span><span class="sxs-lookup"><span data-stu-id="1e124-150">A space is used to separate multiple `[name]=[value]` pairs.</span></span>

<span data-ttu-id="1e124-151">Przykład: `dotnet test -- MSTest.DeploymentEnabled=false MSTest.MapInconclusiveToFailed=True`</span><span class="sxs-lookup"><span data-stu-id="1e124-151">Example: `dotnet test -- MSTest.DeploymentEnabled=false MSTest.MapInconclusiveToFailed=True`</span></span>

<span data-ttu-id="1e124-152">Aby uzyskać więcej informacji na temat RunSettings, zobacz [VSTest. Console. exe: przekazywanie runsettings argumentów](https://github.com/Microsoft/vstest-docs/blob/master/docs/RunSettingsArguments.md).</span><span class="sxs-lookup"><span data-stu-id="1e124-152">For more information about RunSettings, see [vstest.console.exe: Passing RunSettings args](https://github.com/Microsoft/vstest-docs/blob/master/docs/RunSettingsArguments.md).</span></span>

# <a name="net-core-20"></a>[<span data-ttu-id="1e124-153">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="1e124-153">.NET Core 2.0</span></span>](#tab/netcore20)

`-a|--test-adapter-path <PATH_TO_ADAPTER>`

<span data-ttu-id="1e124-154">Użyj niestandardowych adapterów testowych z określonej ścieżki w przebiegu testu.</span><span class="sxs-lookup"><span data-stu-id="1e124-154">Use the custom test adapters from the specified path in the test run.</span></span>

`-c|--configuration {Debug|Release}`

<span data-ttu-id="1e124-155">Definiuje konfigurację kompilacji.</span><span class="sxs-lookup"><span data-stu-id="1e124-155">Defines the build configuration.</span></span> <span data-ttu-id="1e124-156">Wartość domyślna to `Debug`, ale Konfiguracja projektu może zastąpić to domyślne ustawienie zestawu SDK.</span><span class="sxs-lookup"><span data-stu-id="1e124-156">The default value is `Debug`, but your project's configuration could override this default SDK setting.</span></span>

`--collect <DATA_COLLECTOR_FRIENDLY_NAME>`

<span data-ttu-id="1e124-157">Włącza moduł zbierający dane dla przebiegu testu.</span><span class="sxs-lookup"><span data-stu-id="1e124-157">Enables data collector for the test run.</span></span> <span data-ttu-id="1e124-158">Aby uzyskać więcej informacji, zobacz [monitorowanie i analizowanie przebiegu testowego](https://aka.ms/vstest-collect).</span><span class="sxs-lookup"><span data-stu-id="1e124-158">For more information, see [Monitor and analyze test run](https://aka.ms/vstest-collect).</span></span>

`-d|--diag <PATH_TO_DIAGNOSTICS_FILE>`

<span data-ttu-id="1e124-159">Włącza tryb diagnostyczny dla platformy testowej i zapisuje komunikaty diagnostyczne do określonego pliku.</span><span class="sxs-lookup"><span data-stu-id="1e124-159">Enables diagnostic mode for the test platform and write diagnostic messages to the specified file.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="1e124-160">Wyszukuje pliki binarne testów dla konkretnej [struktury](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="1e124-160">Looks for test binaries for a specific [framework](../../standard/frameworks.md).</span></span>

`--filter <EXPRESSION>`

<span data-ttu-id="1e124-161">Filtruje testy w bieżącym projekcie przy użyciu danego wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="1e124-161">Filters out tests in the current project using the given expression.</span></span> <span data-ttu-id="1e124-162">Aby uzyskać więcej informacji, zobacz sekcję [szczegóły opcji filtrowania](#filter-option-details) .</span><span class="sxs-lookup"><span data-stu-id="1e124-162">For more information, see the [Filter option details](#filter-option-details) section.</span></span> <span data-ttu-id="1e124-163">Aby uzyskać więcej informacji i zapoznać się z przykładami dotyczącymi używania selektywnego filtrowania testów jednostkowych, zobacz [Uruchamianie selektywnych testów jednostkowych](../testing/selective-unit-tests.md).</span><span class="sxs-lookup"><span data-stu-id="1e124-163">For more information and examples on how to use selective unit test filtering, see [Running selective unit tests](../testing/selective-unit-tests.md).</span></span>

`-h|--help`

<span data-ttu-id="1e124-164">Drukuje krótką pomoc dla polecenia.</span><span class="sxs-lookup"><span data-stu-id="1e124-164">Prints out a short help for the command.</span></span>

`-l|--logger <LoggerUri/FriendlyName>`

<span data-ttu-id="1e124-165">Określa Rejestrator dla wyników testu.</span><span class="sxs-lookup"><span data-stu-id="1e124-165">Specifies a logger for test results.</span></span>

`--no-build`

<span data-ttu-id="1e124-166">Nie kompiluje projektu testowego przed jego uruchomieniem.</span><span class="sxs-lookup"><span data-stu-id="1e124-166">Doesn't build the test project before running it.</span></span> <span data-ttu-id="1e124-167">Również niejawne ustawia flagę `--no-restore`.</span><span class="sxs-lookup"><span data-stu-id="1e124-167">It also implicit sets the `--no-restore` flag.</span></span>

`--no-restore`

<span data-ttu-id="1e124-168">Nie wykonuje przywracania niejawnego podczas wykonywania polecenia.</span><span class="sxs-lookup"><span data-stu-id="1e124-168">Doesn't execute an implicit restore when running the command.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="1e124-169">Katalog, w którym można znaleźć pliki binarne do uruchomienia.</span><span class="sxs-lookup"><span data-stu-id="1e124-169">Directory in which to find the binaries to run.</span></span>

`-r|--results-directory <PATH>`

<span data-ttu-id="1e124-170">Katalog, w którym zostaną umieszczone wyniki testu.</span><span class="sxs-lookup"><span data-stu-id="1e124-170">The directory where the test results are going to be placed.</span></span> <span data-ttu-id="1e124-171">Jeśli określony katalog nie istnieje, zostanie utworzony.</span><span class="sxs-lookup"><span data-stu-id="1e124-171">If the specified directory doesn't exist, it's created.</span></span>

`-s|--settings <SETTINGS_FILE>`

<span data-ttu-id="1e124-172">Plik `.runsettings` używany do uruchamiania testów.</span><span class="sxs-lookup"><span data-stu-id="1e124-172">The `.runsettings` file to use for running the tests.</span></span> [<span data-ttu-id="1e124-173">Skonfiguruj testy jednostkowe za pomocą pliku `.runsettings`.</span><span class="sxs-lookup"><span data-stu-id="1e124-173">Configure unit tests by using a `.runsettings` file.</span></span>](/visualstudio/test/configure-unit-tests-by-using-a-dot-runsettings-file)

`-t|--list-tests`

<span data-ttu-id="1e124-174">Wyświetl listę wszystkich odnalezionych testów w bieżącym projekcie.</span><span class="sxs-lookup"><span data-stu-id="1e124-174">List all of the discovered tests in the current project.</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="1e124-175">Ustawia poziom szczegółowości polecenia.</span><span class="sxs-lookup"><span data-stu-id="1e124-175">Sets the verbosity level of the command.</span></span> <span data-ttu-id="1e124-176">Dozwolone wartości to `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`i `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="1e124-176">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

# <a name="net-core-1x"></a>[<span data-ttu-id="1e124-177">.NET Core 1. x</span><span class="sxs-lookup"><span data-stu-id="1e124-177">.NET Core 1.x</span></span>](#tab/netcore1x)

`-a|--test-adapter-path <PATH_TO_ADAPTER>`

<span data-ttu-id="1e124-178">Użyj niestandardowych adapterów testowych z określonej ścieżki w przebiegu testu.</span><span class="sxs-lookup"><span data-stu-id="1e124-178">Use the custom test adapters from the specified path in the test run.</span></span>

`-c|--configuration {Debug|Release}`

<span data-ttu-id="1e124-179">Definiuje konfigurację kompilacji.</span><span class="sxs-lookup"><span data-stu-id="1e124-179">Defines the build configuration.</span></span> <span data-ttu-id="1e124-180">Wartość domyślna to `Debug`, ale Konfiguracja projektu może zastąpić to domyślne ustawienie zestawu SDK.</span><span class="sxs-lookup"><span data-stu-id="1e124-180">The default value is `Debug`, but your project's configuration could override this default SDK setting.</span></span>

`-d|--diag <PATH_TO_DIAGNOSTICS_FILE>`

<span data-ttu-id="1e124-181">Włącza tryb diagnostyczny dla platformy testowej i zapisuje komunikaty diagnostyczne do określonego pliku.</span><span class="sxs-lookup"><span data-stu-id="1e124-181">Enables diagnostic mode for the test platform and write diagnostic messages to the specified file.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="1e124-182">Wyszukuje pliki binarne testów dla konkretnej [struktury](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="1e124-182">Looks for test binaries for a specific [framework](../../standard/frameworks.md).</span></span>

`--filter <EXPRESSION>`

<span data-ttu-id="1e124-183">Filtruje testy w bieżącym projekcie przy użyciu danego wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="1e124-183">Filters out tests in the current project using the given expression.</span></span> <span data-ttu-id="1e124-184">Aby uzyskać więcej informacji, zobacz sekcję [szczegóły opcji filtrowania](#filter-option-details) .</span><span class="sxs-lookup"><span data-stu-id="1e124-184">For more information, see the [Filter option details](#filter-option-details) section.</span></span> <span data-ttu-id="1e124-185">Aby uzyskać więcej informacji i zapoznać się z przykładami dotyczącymi używania selektywnego filtrowania testów jednostkowych, zobacz [Uruchamianie selektywnych testów jednostkowych](../testing/selective-unit-tests.md).</span><span class="sxs-lookup"><span data-stu-id="1e124-185">For more information and examples on how to use selective unit test filtering, see [Running selective unit tests](../testing/selective-unit-tests.md).</span></span>

`-h|--help`

<span data-ttu-id="1e124-186">Drukuje krótką pomoc dla polecenia.</span><span class="sxs-lookup"><span data-stu-id="1e124-186">Prints out a short help for the command.</span></span>

`-l|--logger <LoggerUri/FriendlyName>`

<span data-ttu-id="1e124-187">Określa Rejestrator dla wyników testu.</span><span class="sxs-lookup"><span data-stu-id="1e124-187">Specifies a logger for test results.</span></span>

`--no-build`

<span data-ttu-id="1e124-188">Nie kompiluje projektu testowego przed jego uruchomieniem.</span><span class="sxs-lookup"><span data-stu-id="1e124-188">Doesn't build the test project before running it.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="1e124-189">Katalog, w którym można znaleźć pliki binarne do uruchomienia.</span><span class="sxs-lookup"><span data-stu-id="1e124-189">Directory in which to find the binaries to run.</span></span>

`-s|--settings <SETTINGS_FILE>`

<span data-ttu-id="1e124-190">Plik `.runsettings` używany do uruchamiania testów.</span><span class="sxs-lookup"><span data-stu-id="1e124-190">The `.runsettings` file to use for running the tests.</span></span> [<span data-ttu-id="1e124-191">Skonfiguruj testy jednostkowe za pomocą pliku `.runsettings`.</span><span class="sxs-lookup"><span data-stu-id="1e124-191">Configure unit tests by using a `.runsettings` file.</span></span>](/visualstudio/test/configure-unit-tests-by-using-a-dot-runsettings-file)

`-t|--list-tests`

<span data-ttu-id="1e124-192">Wyświetl listę wszystkich odnalezionych testów w bieżącym projekcie.</span><span class="sxs-lookup"><span data-stu-id="1e124-192">List all of the discovered tests in the current project.</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="1e124-193">Ustawia poziom szczegółowości polecenia.</span><span class="sxs-lookup"><span data-stu-id="1e124-193">Sets the verbosity level of the command.</span></span> <span data-ttu-id="1e124-194">Dozwolone wartości to `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`i `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="1e124-194">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

---

## <a name="examples"></a><span data-ttu-id="1e124-195">Przykłady</span><span class="sxs-lookup"><span data-stu-id="1e124-195">Examples</span></span>

<span data-ttu-id="1e124-196">Uruchom testy w projekcie w bieżącym katalogu:</span><span class="sxs-lookup"><span data-stu-id="1e124-196">Run the tests in the project in the current directory:</span></span>

`dotnet test`

<span data-ttu-id="1e124-197">Uruchom testy w `test1` projekcie:</span><span class="sxs-lookup"><span data-stu-id="1e124-197">Run the tests in the `test1` project:</span></span>

`dotnet test ~/projects/test1/test1.csproj`

<span data-ttu-id="1e124-198">Uruchom testy w projekcie w bieżącym katalogu i wygeneruj plik wyników testu w formacie TRX:</span><span class="sxs-lookup"><span data-stu-id="1e124-198">Run the tests in the project in the current directory and generate a test results file in the trx format:</span></span>

`dotnet test --logger trx`

## <a name="filter-option-details"></a><span data-ttu-id="1e124-199">Szczegóły opcji filtrowania</span><span class="sxs-lookup"><span data-stu-id="1e124-199">Filter option details</span></span>

`--filter <EXPRESSION>`

<span data-ttu-id="1e124-200">`<Expression>` ma `<property><operator><value>[|&<Expression>]`format.</span><span class="sxs-lookup"><span data-stu-id="1e124-200">`<Expression>` has the format `<property><operator><value>[|&<Expression>]`.</span></span>

<span data-ttu-id="1e124-201">`<property>` jest atrybutem `Test Case`.</span><span class="sxs-lookup"><span data-stu-id="1e124-201">`<property>` is an attribute of the `Test Case`.</span></span> <span data-ttu-id="1e124-202">Poniżej przedstawiono właściwości obsługiwane przez popularne struktury testów jednostkowych:</span><span class="sxs-lookup"><span data-stu-id="1e124-202">The following are the properties supported by popular unit test frameworks:</span></span>

| <span data-ttu-id="1e124-203">Struktury testowej</span><span class="sxs-lookup"><span data-stu-id="1e124-203">Test Framework</span></span> | <span data-ttu-id="1e124-204">Obsługiwane właściwości</span><span class="sxs-lookup"><span data-stu-id="1e124-204">Supported properties</span></span>                                                                                      |
| -------------- | --------------------------------------------------------------------------------------------------------- |
| <span data-ttu-id="1e124-205">MSTest</span><span class="sxs-lookup"><span data-stu-id="1e124-205">MSTest</span></span>         | <ul><li><span data-ttu-id="1e124-206">FullyQualifiedName</span><span class="sxs-lookup"><span data-stu-id="1e124-206">FullyQualifiedName</span></span></li><li><span data-ttu-id="1e124-207">Name (Nazwa)</span><span class="sxs-lookup"><span data-stu-id="1e124-207">Name</span></span></li><li><span data-ttu-id="1e124-208">Nazwą</span><span class="sxs-lookup"><span data-stu-id="1e124-208">ClassName</span></span></li><li><span data-ttu-id="1e124-209">Priorytet</span><span class="sxs-lookup"><span data-stu-id="1e124-209">Priority</span></span></li><li><span data-ttu-id="1e124-210">TestCategory</span><span class="sxs-lookup"><span data-stu-id="1e124-210">TestCategory</span></span></li></ul> |
| <span data-ttu-id="1e124-211">xUnit</span><span class="sxs-lookup"><span data-stu-id="1e124-211">xUnit</span></span>          | <ul><li><span data-ttu-id="1e124-212">FullyQualifiedName</span><span class="sxs-lookup"><span data-stu-id="1e124-212">FullyQualifiedName</span></span></li><li><span data-ttu-id="1e124-213">DisplayName</span><span class="sxs-lookup"><span data-stu-id="1e124-213">DisplayName</span></span></li><li><span data-ttu-id="1e124-214">Cech</span><span class="sxs-lookup"><span data-stu-id="1e124-214">Traits</span></span></li></ul>                                   |

<span data-ttu-id="1e124-215">`<operator>` opisuje relację między właściwością a wartością:</span><span class="sxs-lookup"><span data-stu-id="1e124-215">The `<operator>` describes the relationship between the property and the value:</span></span>

| <span data-ttu-id="1e124-216">Operator</span><span class="sxs-lookup"><span data-stu-id="1e124-216">Operator</span></span> | <span data-ttu-id="1e124-217">Funkcja</span><span class="sxs-lookup"><span data-stu-id="1e124-217">Function</span></span>        |
| :------: | --------------- |
| `=`      | <span data-ttu-id="1e124-218">Dokładne dopasowanie</span><span class="sxs-lookup"><span data-stu-id="1e124-218">Exact match</span></span>     |
| `!=`     | <span data-ttu-id="1e124-219">Niedokładne dopasowanie</span><span class="sxs-lookup"><span data-stu-id="1e124-219">Not exact match</span></span> |
| `~`      | <span data-ttu-id="1e124-220">Contains</span><span class="sxs-lookup"><span data-stu-id="1e124-220">Contains</span></span>        |
| `!~`     | <span data-ttu-id="1e124-221">Nie zawiera</span><span class="sxs-lookup"><span data-stu-id="1e124-221">Not contains</span></span>    |

<span data-ttu-id="1e124-222">`<value>` jest ciągiem.</span><span class="sxs-lookup"><span data-stu-id="1e124-222">`<value>` is a string.</span></span> <span data-ttu-id="1e124-223">Wszystkie wyszukiwania są rozróżniane wielkości liter.</span><span class="sxs-lookup"><span data-stu-id="1e124-223">All the lookups are case insensitive.</span></span>

<span data-ttu-id="1e124-224">Wyrażenie bez `<operator>` jest automatycznie uznawane za `contains` właściwości `FullyQualifiedName` (na przykład `dotnet test --filter xyz` jest taka sama jak `dotnet test --filter FullyQualifiedName~xyz`).</span><span class="sxs-lookup"><span data-stu-id="1e124-224">An expression without an `<operator>` is automatically considered as a `contains` on `FullyQualifiedName` property (for example, `dotnet test --filter xyz` is same as `dotnet test --filter FullyQualifiedName~xyz`).</span></span>

<span data-ttu-id="1e124-225">Wyrażenia mogą być dołączane za pomocą operatorów warunkowych:</span><span class="sxs-lookup"><span data-stu-id="1e124-225">Expressions can be joined with conditional operators:</span></span>

| <span data-ttu-id="1e124-226">Operator</span><span class="sxs-lookup"><span data-stu-id="1e124-226">Operator</span></span>            | <span data-ttu-id="1e124-227">Funkcja</span><span class="sxs-lookup"><span data-stu-id="1e124-227">Function</span></span> |
| ------------------- | -------- |
| <code>&#124;</code> | <span data-ttu-id="1e124-228">LUB</span><span class="sxs-lookup"><span data-stu-id="1e124-228">OR</span></span>       |
| `&`                 | <span data-ttu-id="1e124-229">AND</span><span class="sxs-lookup"><span data-stu-id="1e124-229">AND</span></span>      |

<span data-ttu-id="1e124-230">Wyrażenia można ująć w nawiasy, gdy są używane operatory warunkowe (na przykład `(Name~TestMethod1) | (Name~TestMethod2)`).</span><span class="sxs-lookup"><span data-stu-id="1e124-230">You can enclose expressions in parenthesis when using conditional operators (for example, `(Name~TestMethod1) | (Name~TestMethod2)`).</span></span>

<span data-ttu-id="1e124-231">Aby uzyskać więcej informacji i zapoznać się z przykładami dotyczącymi używania selektywnego filtrowania testów jednostkowych, zobacz [Uruchamianie selektywnych testów jednostkowych](../testing/selective-unit-tests.md).</span><span class="sxs-lookup"><span data-stu-id="1e124-231">For more information and examples on how to use selective unit test filtering, see [Running selective unit tests](../testing/selective-unit-tests.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="1e124-232">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="1e124-232">See also</span></span>

- [<span data-ttu-id="1e124-233">Struktury i elementy docelowe</span><span class="sxs-lookup"><span data-stu-id="1e124-233">Frameworks and Targets</span></span>](../../standard/frameworks.md)
- [<span data-ttu-id="1e124-234">Wykaz identyfikatorów środowiska uruchomieniowego platformy .NET Core (RID)</span><span class="sxs-lookup"><span data-stu-id="1e124-234">.NET Core Runtime IDentifier (RID) catalog</span></span>](../rid-catalog.md)
