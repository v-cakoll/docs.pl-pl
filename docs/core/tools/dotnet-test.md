---
title: polecenie test DotNet
description: Polecenia dotnet test służy do wykonywania testów jednostkowych w danym projekcie.
ms.date: 05/29/2018
ms.openlocfilehash: 1b2a3917a930db0c0a49ebea41f568aaf4a58ee3
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54535285"
---
# <a name="dotnet-test"></a><span data-ttu-id="b83d8-103">polecenia DotNet test</span><span class="sxs-lookup"><span data-stu-id="b83d8-103">dotnet test</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="b83d8-104">Nazwa</span><span class="sxs-lookup"><span data-stu-id="b83d8-104">Name</span></span>

<span data-ttu-id="b83d8-105">`dotnet test` -Sterownik test .NET służących do wykonywania testów jednostkowych.</span><span class="sxs-lookup"><span data-stu-id="b83d8-105">`dotnet test` - .NET test driver used to execute unit tests.</span></span>

## <a name="synopsis"></a><span data-ttu-id="b83d8-106">Streszczenie</span><span class="sxs-lookup"><span data-stu-id="b83d8-106">Synopsis</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="b83d8-107">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="b83d8-107">.NET Core 2.1</span></span>](#tab/netcore21)

```console
dotnet test [<PROJECT>] [-a|--test-adapter-path] [--blame] [-c|--configuration] [--collect] [-d|--diag] [-f|--framework] [--filter]
    [-l|--logger] [--no-build] [--no-restore] [-o|--output] [-r|--results-directory] [-s|--settings] [-t|--list-tests] 
    [-v|--verbosity] [-- <RunSettings arguments>]

dotnet test [-h|--help]
```

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="b83d8-108">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="b83d8-108">.NET Core 2.0</span></span>](#tab/netcore20)

```console
dotnet test [<PROJECT>] [-a|--test-adapter-path] [-c|--configuration] [--collect] [-d|--diag] [-f|--framework] [--filter]
    [-l|--logger] [--no-build] [--no-restore] [-o|--output] [-r|--results-directory] [-s|--settings] [-t|--list-tests] [-v|--verbosity]

dotnet test [-h|--help]
```

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="b83d8-109">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="b83d8-109">.NET Core 1.x</span></span>](#tab/netcore1x)

```console
dotnet test [<PROJECT>] [-a|--test-adapter-path] [-c|--configuration] [-d|--diag] [-f|--framework] [--filter] [-l|--logger] [--no-build] [-o|--output] [-s|--settings] [-t|--list-tests]  [-v|--verbosity]

dotnet test [-h|--help]
```

---

## <a name="description"></a><span data-ttu-id="b83d8-110">Opis</span><span class="sxs-lookup"><span data-stu-id="b83d8-110">Description</span></span>

<span data-ttu-id="b83d8-111">`dotnet test` Polecenie służy do wykonywania testów jednostkowych w danym projekcie.</span><span class="sxs-lookup"><span data-stu-id="b83d8-111">The `dotnet test` command is used to execute unit tests in a given project.</span></span> <span data-ttu-id="b83d8-112">`dotnet test` Polecenie uruchamia aplikację konsolową modułu uruchamiającego test, określony dla projektu.</span><span class="sxs-lookup"><span data-stu-id="b83d8-112">The `dotnet test` command launches the test runner console application specified for a project.</span></span> <span data-ttu-id="b83d8-113">Moduł uruchamiający testy zdefiniowane dla środowiska testów jednostkowych (np. MSTest, NUnit lub xUnit) są wykonywane i zgłasza powodzenie lub niepowodzenie każdego testu.</span><span class="sxs-lookup"><span data-stu-id="b83d8-113">The test runner executes the tests defined for a unit test framework (for example, MSTest, NUnit, or xUnit) and reports the success or failure of each test.</span></span> <span data-ttu-id="b83d8-114">Jeśli wszystkie testy zakończą się powodzeniem, narzędzia test runner zwraca wartość 0, kod zakończenia; Jeśli dowolny test zakończy się niepowodzeniem, w przeciwnym razie zwraca 1.</span><span class="sxs-lookup"><span data-stu-id="b83d8-114">If all tests are successful, the test runner returns 0 as an exit code; otherwise if any test fails, it returns 1.</span></span> <span data-ttu-id="b83d8-115">Narzędzie test runner Biblioteka testów jednostkowych jest spakowany jako pakiety NuGet i zostaną przywrócone jako zwykłe zależności projektu.</span><span class="sxs-lookup"><span data-stu-id="b83d8-115">The test runner and the unit test library are packaged as NuGet packages and are restored as ordinary dependencies for the project.</span></span>

<span data-ttu-id="b83d8-116">Projekty testowe określić modułu uruchamiającego testy przy użyciu zwykłej `<PackageReference>` elementu, jak pokazano w poniższym przykładowym pliku projektu:</span><span class="sxs-lookup"><span data-stu-id="b83d8-116">Test projects specify the test runner using an ordinary `<PackageReference>` element, as seen in the following sample project file:</span></span>

[!code-xml[XUnit Basic Template](../../../samples/snippets/csharp/xunit-test/xunit-test.csproj)]

## <a name="arguments"></a><span data-ttu-id="b83d8-117">Argumenty</span><span class="sxs-lookup"><span data-stu-id="b83d8-117">Arguments</span></span>

`PROJECT`

<span data-ttu-id="b83d8-118">Ścieżka do projektu testowego.</span><span class="sxs-lookup"><span data-stu-id="b83d8-118">Path to the test project.</span></span> <span data-ttu-id="b83d8-119">Jeśli nie zostanie określony, domyślnie bieżącego katalogu.</span><span class="sxs-lookup"><span data-stu-id="b83d8-119">If not specified, it defaults to current directory.</span></span>

## <a name="options"></a><span data-ttu-id="b83d8-120">Opcje</span><span class="sxs-lookup"><span data-stu-id="b83d8-120">Options</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="b83d8-121">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="b83d8-121">.NET Core 2.1</span></span>](#tab/netcore21)

`-a|--test-adapter-path <PATH_TO_ADAPTER>`

<span data-ttu-id="b83d8-122">Używa niestandardowych adapterów testowych z określonej ścieżki w przebiegu testu.</span><span class="sxs-lookup"><span data-stu-id="b83d8-122">Use the custom test adapters from the specified path in the test run.</span></span>

`--blame`

<span data-ttu-id="b83d8-123">Uruchamia testy w trybie polecenia blame.</span><span class="sxs-lookup"><span data-stu-id="b83d8-123">Runs the tests in blame mode.</span></span> <span data-ttu-id="b83d8-124">Ta opcja jest przydatna polega na wyizolowaniu problematyczne testy, powodując hosta testów ulega awarii.</span><span class="sxs-lookup"><span data-stu-id="b83d8-124">This option is helpful in isolating the problematic tests causing test host to crash.</span></span> <span data-ttu-id="b83d8-125">Tworzy plik wyjściowy w bieżącym katalogu jako *Sequence.xml* , przechwytuje kolejność wykonywania testów przed awarią.</span><span class="sxs-lookup"><span data-stu-id="b83d8-125">It creates an output file in the current directory as *Sequence.xml* that captures the order of tests execution before the crash.</span></span>

`-c|--configuration {Debug|Release}`

<span data-ttu-id="b83d8-126">Definiuje konfigurację kompilacji.</span><span class="sxs-lookup"><span data-stu-id="b83d8-126">Defines the build configuration.</span></span> <span data-ttu-id="b83d8-127">Wartość domyślna to `Debug`, ale konfiguracji projektu można zastąpić to ustawienie SDK domyślne.</span><span class="sxs-lookup"><span data-stu-id="b83d8-127">The default value is `Debug`, but your project's configuration could override this default SDK setting.</span></span>

`--collect <DATA_COLLECTOR_FRIENDLY_NAME>`

<span data-ttu-id="b83d8-128">Włącza moduł zbierający dane dla przebiegu testu.</span><span class="sxs-lookup"><span data-stu-id="b83d8-128">Enables data collector for the test run.</span></span> <span data-ttu-id="b83d8-129">Aby uzyskać więcej informacji, zobacz [monitorowanie i analizowanie przebiegu testu](https://aka.ms/vstest-collect).</span><span class="sxs-lookup"><span data-stu-id="b83d8-129">For more information, see [Monitor and analyze test run](https://aka.ms/vstest-collect).</span></span>

`-d|--diag <PATH_TO_DIAGNOSTICS_FILE>`

<span data-ttu-id="b83d8-130">Włącza tryb diagnostycznych dla testu platformy i zapisu komunikaty diagnostyczne do określonego pliku.</span><span class="sxs-lookup"><span data-stu-id="b83d8-130">Enables diagnostic mode for the test platform and write diagnostic messages to the specified file.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="b83d8-131">Wyszukuje pliki binarne testu dla określonego [framework](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="b83d8-131">Looks for test binaries for a specific [framework](../../standard/frameworks.md).</span></span>

`--filter <EXPRESSION>`

<span data-ttu-id="b83d8-132">Filtruje testy w bieżącym projekcie za pomocą podanego wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="b83d8-132">Filters out tests in the current project using the given expression.</span></span> <span data-ttu-id="b83d8-133">Aby uzyskać więcej informacji, zobacz [szczegóły opcji filtru](#filter-option-details) sekcji.</span><span class="sxs-lookup"><span data-stu-id="b83d8-133">For more information, see the [Filter option details](#filter-option-details) section.</span></span> <span data-ttu-id="b83d8-134">Aby uzyskać dodatkowe informacje i przykłady dotyczące korzystania z jednostki selektywne testowanie filtrowania, zobacz [uruchamianie selektywnych testów jednostkowych](../testing/selective-unit-tests.md).</span><span class="sxs-lookup"><span data-stu-id="b83d8-134">For more information and examples on how to use selective unit test filtering, see [Running selective unit tests](../testing/selective-unit-tests.md).</span></span>

`-h|--help`

<span data-ttu-id="b83d8-135">Drukuje krótki pomoc dotyczącą polecenia.</span><span class="sxs-lookup"><span data-stu-id="b83d8-135">Prints out a short help for the command.</span></span>

`-l|--logger <LoggerUri/FriendlyName>`

<span data-ttu-id="b83d8-136">Określa Rejestrator dla wyników badań.</span><span class="sxs-lookup"><span data-stu-id="b83d8-136">Specifies a logger for test results.</span></span>

`--no-build`

<span data-ttu-id="b83d8-137">Nie da się skompilować projektu testowego przed jego uruchomieniem.</span><span class="sxs-lookup"><span data-stu-id="b83d8-137">Doesn't build the test project before running it.</span></span> <span data-ttu-id="b83d8-138">Ustawia ona również niejawne `--no-restore` flagi.</span><span class="sxs-lookup"><span data-stu-id="b83d8-138">It also implicit sets the `--no-restore` flag.</span></span>

`--no-restore`

<span data-ttu-id="b83d8-139">Przy uruchamianiu polecenia niejawne przywracania nie jest wykonywany.</span><span class="sxs-lookup"><span data-stu-id="b83d8-139">Doesn't execute an implicit restore when running the command.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="b83d8-140">Katalog, w którym można znaleźć plików binarnych do uruchomienia.</span><span class="sxs-lookup"><span data-stu-id="b83d8-140">Directory in which to find the binaries to run.</span></span>

`-r|--results-directory <PATH>`

<span data-ttu-id="b83d8-141">Katalog, gdzie wyników testu do umieszczenia.</span><span class="sxs-lookup"><span data-stu-id="b83d8-141">The directory where the test results are going to be placed.</span></span> <span data-ttu-id="b83d8-142">Jeśli określony katalog nie istnieje, zostanie utworzony.</span><span class="sxs-lookup"><span data-stu-id="b83d8-142">If the specified directory doesn't exist, it's created.</span></span>

`-s|--settings <SETTINGS_FILE>`

<span data-ttu-id="b83d8-143">Ustawienia używane podczas uruchamiania testów.</span><span class="sxs-lookup"><span data-stu-id="b83d8-143">Settings to use when running tests.</span></span>

`-t|--list-tests`

<span data-ttu-id="b83d8-144">Listę wszystkich odnalezionych testów w bieżącym projekcie.</span><span class="sxs-lookup"><span data-stu-id="b83d8-144">List all of the discovered tests in the current project.</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="b83d8-145">Ustawia poziom szczegółowości polecenia.</span><span class="sxs-lookup"><span data-stu-id="b83d8-145">Sets the verbosity level of the command.</span></span> <span data-ttu-id="b83d8-146">Dozwolone wartości to `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, i `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="b83d8-146">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

`RunSettings arguments`

<span data-ttu-id="b83d8-147">Argumenty są przekazywane jako RunSettings konfiguracji testu.</span><span class="sxs-lookup"><span data-stu-id="b83d8-147">Arguments passed as RunSettings configurations for the test.</span></span> <span data-ttu-id="b83d8-148">Argumenty są określane jako `[name]=[value]` pary po "--" (Uwaga miejsca po —).</span><span class="sxs-lookup"><span data-stu-id="b83d8-148">Arguments are specified as `[name]=[value]` pairs after "-- " (note the space after --).</span></span> <span data-ttu-id="b83d8-149">Spacja jest używana do oddzielania wielu `[name]=[value]` pary.</span><span class="sxs-lookup"><span data-stu-id="b83d8-149">A space is used to separate multiple `[name]=[value]` pairs.</span></span>

<span data-ttu-id="b83d8-150">Przykład: `dotnet test -- MSTest.DeploymentEnabled=false MSTest.MapInconclusiveToFailed=True`</span><span class="sxs-lookup"><span data-stu-id="b83d8-150">Example: `dotnet test -- MSTest.DeploymentEnabled=false MSTest.MapInconclusiveToFailed=True`</span></span>

<span data-ttu-id="b83d8-151">Aby uzyskać więcej informacji na temat RunSettings zobacz [vstest.console.exe: Przekazywanie argumentów RunSettings](https://github.com/Microsoft/vstest-docs/blob/master/docs/RunSettingsArguments.md).</span><span class="sxs-lookup"><span data-stu-id="b83d8-151">For more information about RunSettings, see [vstest.console.exe: Passing RunSettings args](https://github.com/Microsoft/vstest-docs/blob/master/docs/RunSettingsArguments.md).</span></span>

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="b83d8-152">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="b83d8-152">.NET Core 2.0</span></span>](#tab/netcore20)

`-a|--test-adapter-path <PATH_TO_ADAPTER>`

<span data-ttu-id="b83d8-153">Używa niestandardowych adapterów testowych z określonej ścieżki w przebiegu testu.</span><span class="sxs-lookup"><span data-stu-id="b83d8-153">Use the custom test adapters from the specified path in the test run.</span></span>

`-c|--configuration {Debug|Release}`

<span data-ttu-id="b83d8-154">Definiuje konfigurację kompilacji.</span><span class="sxs-lookup"><span data-stu-id="b83d8-154">Defines the build configuration.</span></span> <span data-ttu-id="b83d8-155">Wartość domyślna to `Debug`, ale konfiguracji projektu można zastąpić to ustawienie SDK domyślne.</span><span class="sxs-lookup"><span data-stu-id="b83d8-155">The default value is `Debug`, but your project's configuration could override this default SDK setting.</span></span>

`--collect <DATA_COLLECTOR_FRIENDLY_NAME>`

<span data-ttu-id="b83d8-156">Włącza moduł zbierający dane dla przebiegu testu.</span><span class="sxs-lookup"><span data-stu-id="b83d8-156">Enables data collector for the test run.</span></span> <span data-ttu-id="b83d8-157">Aby uzyskać więcej informacji, zobacz [monitorowanie i analizowanie przebiegu testu](https://aka.ms/vstest-collect).</span><span class="sxs-lookup"><span data-stu-id="b83d8-157">For more information, see [Monitor and analyze test run](https://aka.ms/vstest-collect).</span></span>

`-d|--diag <PATH_TO_DIAGNOSTICS_FILE>`

<span data-ttu-id="b83d8-158">Włącza tryb diagnostycznych dla testu platformy i zapisu komunikaty diagnostyczne do określonego pliku.</span><span class="sxs-lookup"><span data-stu-id="b83d8-158">Enables diagnostic mode for the test platform and write diagnostic messages to the specified file.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="b83d8-159">Wyszukuje pliki binarne testu dla określonego [framework](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="b83d8-159">Looks for test binaries for a specific [framework](../../standard/frameworks.md).</span></span>

`--filter <EXPRESSION>`

<span data-ttu-id="b83d8-160">Filtruje testy w bieżącym projekcie za pomocą podanego wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="b83d8-160">Filters out tests in the current project using the given expression.</span></span> <span data-ttu-id="b83d8-161">Aby uzyskać więcej informacji, zobacz [szczegóły opcji filtru](#filter-option-details) sekcji.</span><span class="sxs-lookup"><span data-stu-id="b83d8-161">For more information, see the [Filter option details](#filter-option-details) section.</span></span> <span data-ttu-id="b83d8-162">Aby uzyskać dodatkowe informacje i przykłady dotyczące korzystania z jednostki selektywne testowanie filtrowania, zobacz [uruchamianie selektywnych testów jednostkowych](../testing/selective-unit-tests.md).</span><span class="sxs-lookup"><span data-stu-id="b83d8-162">For more information and examples on how to use selective unit test filtering, see [Running selective unit tests](../testing/selective-unit-tests.md).</span></span>

`-h|--help`

<span data-ttu-id="b83d8-163">Drukuje krótki pomoc dotyczącą polecenia.</span><span class="sxs-lookup"><span data-stu-id="b83d8-163">Prints out a short help for the command.</span></span>

`-l|--logger <LoggerUri/FriendlyName>`

<span data-ttu-id="b83d8-164">Określa Rejestrator dla wyników badań.</span><span class="sxs-lookup"><span data-stu-id="b83d8-164">Specifies a logger for test results.</span></span>

`--no-build`

<span data-ttu-id="b83d8-165">Nie da się skompilować projektu testowego przed jego uruchomieniem.</span><span class="sxs-lookup"><span data-stu-id="b83d8-165">Doesn't build the test project before running it.</span></span> <span data-ttu-id="b83d8-166">Ustawia ona również niejawne `--no-restore` flagi.</span><span class="sxs-lookup"><span data-stu-id="b83d8-166">It also implicit sets the `--no-restore` flag.</span></span>

`--no-restore`

<span data-ttu-id="b83d8-167">Przy uruchamianiu polecenia niejawne przywracania nie jest wykonywany.</span><span class="sxs-lookup"><span data-stu-id="b83d8-167">Doesn't execute an implicit restore when running the command.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="b83d8-168">Katalog, w którym można znaleźć plików binarnych do uruchomienia.</span><span class="sxs-lookup"><span data-stu-id="b83d8-168">Directory in which to find the binaries to run.</span></span>

`-r|--results-directory <PATH>`

<span data-ttu-id="b83d8-169">Katalog, gdzie wyników testu do umieszczenia.</span><span class="sxs-lookup"><span data-stu-id="b83d8-169">The directory where the test results are going to be placed.</span></span> <span data-ttu-id="b83d8-170">Jeśli określony katalog nie istnieje, zostanie utworzony.</span><span class="sxs-lookup"><span data-stu-id="b83d8-170">If the specified directory doesn't exist, it's created.</span></span>

`-s|--settings <SETTINGS_FILE>`

<span data-ttu-id="b83d8-171">Ustawienia używane podczas uruchamiania testów.</span><span class="sxs-lookup"><span data-stu-id="b83d8-171">Settings to use when running tests.</span></span>

`-t|--list-tests`

<span data-ttu-id="b83d8-172">Listę wszystkich odnalezionych testów w bieżącym projekcie.</span><span class="sxs-lookup"><span data-stu-id="b83d8-172">List all of the discovered tests in the current project.</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="b83d8-173">Ustawia poziom szczegółowości polecenia.</span><span class="sxs-lookup"><span data-stu-id="b83d8-173">Sets the verbosity level of the command.</span></span> <span data-ttu-id="b83d8-174">Dozwolone wartości to `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, i `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="b83d8-174">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="b83d8-175">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="b83d8-175">.NET Core 1.x</span></span>](#tab/netcore1x)

`-a|--test-adapter-path <PATH_TO_ADAPTER>`

<span data-ttu-id="b83d8-176">Używa niestandardowych adapterów testowych z określonej ścieżki w przebiegu testu.</span><span class="sxs-lookup"><span data-stu-id="b83d8-176">Use the custom test adapters from the specified path in the test run.</span></span>

`-c|--configuration {Debug|Release}`

<span data-ttu-id="b83d8-177">Definiuje konfigurację kompilacji.</span><span class="sxs-lookup"><span data-stu-id="b83d8-177">Defines the build configuration.</span></span> <span data-ttu-id="b83d8-178">Wartość domyślna to `Debug`, ale konfiguracji projektu można zastąpić to ustawienie SDK domyślne.</span><span class="sxs-lookup"><span data-stu-id="b83d8-178">The default value is `Debug`, but your project's configuration could override this default SDK setting.</span></span>

`-d|--diag <PATH_TO_DIAGNOSTICS_FILE>`

<span data-ttu-id="b83d8-179">Włącza tryb diagnostycznych dla testu platformy i zapisu komunikaty diagnostyczne do określonego pliku.</span><span class="sxs-lookup"><span data-stu-id="b83d8-179">Enables diagnostic mode for the test platform and write diagnostic messages to the specified file.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="b83d8-180">Wyszukuje pliki binarne testu dla określonego [framework](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="b83d8-180">Looks for test binaries for a specific [framework](../../standard/frameworks.md).</span></span>

`--filter <EXPRESSION>`

<span data-ttu-id="b83d8-181">Filtruje testy w bieżącym projekcie za pomocą podanego wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="b83d8-181">Filters out tests in the current project using the given expression.</span></span> <span data-ttu-id="b83d8-182">Aby uzyskać więcej informacji, zobacz [szczegóły opcji filtru](#filter-option-details) sekcji.</span><span class="sxs-lookup"><span data-stu-id="b83d8-182">For more information, see the [Filter option details](#filter-option-details) section.</span></span> <span data-ttu-id="b83d8-183">Aby uzyskać dodatkowe informacje i przykłady dotyczące korzystania z jednostki selektywne testowanie filtrowania, zobacz [uruchamianie selektywnych testów jednostkowych](../testing/selective-unit-tests.md).</span><span class="sxs-lookup"><span data-stu-id="b83d8-183">For more information and examples on how to use selective unit test filtering, see [Running selective unit tests](../testing/selective-unit-tests.md).</span></span>

`-h|--help`

<span data-ttu-id="b83d8-184">Drukuje krótki pomoc dotyczącą polecenia.</span><span class="sxs-lookup"><span data-stu-id="b83d8-184">Prints out a short help for the command.</span></span>

`-l|--logger <LoggerUri/FriendlyName>`

<span data-ttu-id="b83d8-185">Określa Rejestrator dla wyników badań.</span><span class="sxs-lookup"><span data-stu-id="b83d8-185">Specifies a logger for test results.</span></span>

`--no-build`

<span data-ttu-id="b83d8-186">Nie da się skompilować projektu testowego przed jego uruchomieniem.</span><span class="sxs-lookup"><span data-stu-id="b83d8-186">Doesn't build the test project before running it.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="b83d8-187">Katalog, w którym można znaleźć plików binarnych do uruchomienia.</span><span class="sxs-lookup"><span data-stu-id="b83d8-187">Directory in which to find the binaries to run.</span></span>

`-s|--settings <SETTINGS_FILE>`

<span data-ttu-id="b83d8-188">Ustawienia używane podczas uruchamiania testów.</span><span class="sxs-lookup"><span data-stu-id="b83d8-188">Settings to use when running tests.</span></span>

`-t|--list-tests`

<span data-ttu-id="b83d8-189">Listę wszystkich odnalezionych testów w bieżącym projekcie.</span><span class="sxs-lookup"><span data-stu-id="b83d8-189">List all of the discovered tests in the current project.</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="b83d8-190">Ustawia poziom szczegółowości polecenia.</span><span class="sxs-lookup"><span data-stu-id="b83d8-190">Sets the verbosity level of the command.</span></span> <span data-ttu-id="b83d8-191">Dozwolone wartości to `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, i `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="b83d8-191">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

---

## <a name="examples"></a><span data-ttu-id="b83d8-192">Przykłady</span><span class="sxs-lookup"><span data-stu-id="b83d8-192">Examples</span></span>

<span data-ttu-id="b83d8-193">Uruchom testy w projekcie w bieżącym katalogu:</span><span class="sxs-lookup"><span data-stu-id="b83d8-193">Run the tests in the project in the current directory:</span></span>

`dotnet test`

<span data-ttu-id="b83d8-194">Uruchom testy `test1` projektu:</span><span class="sxs-lookup"><span data-stu-id="b83d8-194">Run the tests in the `test1` project:</span></span>

`dotnet test ~/projects/test1/test1.csproj`

<span data-ttu-id="b83d8-195">Uruchom testy w projekcie w bieżącym katalogu i wygenerować plik wyników testu w formacie trx:</span><span class="sxs-lookup"><span data-stu-id="b83d8-195">Run the tests in the project in the current directory and generate a test results file in the trx format:</span></span>

`dotnet test --logger:trx`

## <a name="filter-option-details"></a><span data-ttu-id="b83d8-196">Szczegóły opcji filtru</span><span class="sxs-lookup"><span data-stu-id="b83d8-196">Filter option details</span></span>

`--filter <EXPRESSION>`

<span data-ttu-id="b83d8-197">`<Expression>` ma format `<property><operator><value>[|&<Expression>]`.</span><span class="sxs-lookup"><span data-stu-id="b83d8-197">`<Expression>` has the format `<property><operator><value>[|&<Expression>]`.</span></span>

<span data-ttu-id="b83d8-198">`<property>` jest to atrybut `Test Case`.</span><span class="sxs-lookup"><span data-stu-id="b83d8-198">`<property>` is an attribute of the `Test Case`.</span></span> <span data-ttu-id="b83d8-199">Poniżej przedstawiono właściwości obsługiwanych przez platform testów jednostkowych innych popularnych:</span><span class="sxs-lookup"><span data-stu-id="b83d8-199">The following are the properties supported by popular unit test frameworks:</span></span>

| <span data-ttu-id="b83d8-200">Struktury testowej</span><span class="sxs-lookup"><span data-stu-id="b83d8-200">Test Framework</span></span> | <span data-ttu-id="b83d8-201">Obsługiwanych właściwości</span><span class="sxs-lookup"><span data-stu-id="b83d8-201">Supported properties</span></span>                                                                                      |
| -------------- | --------------------------------------------------------------------------------------------------------- |
| <span data-ttu-id="b83d8-202">MSTest</span><span class="sxs-lookup"><span data-stu-id="b83d8-202">MSTest</span></span>         | <ul><li><span data-ttu-id="b83d8-203">FullyQualifiedName</span><span class="sxs-lookup"><span data-stu-id="b83d8-203">FullyQualifiedName</span></span></li><li><span data-ttu-id="b83d8-204">Nazwa</span><span class="sxs-lookup"><span data-stu-id="b83d8-204">Name</span></span></li><li><span data-ttu-id="b83d8-205">ClassName</span><span class="sxs-lookup"><span data-stu-id="b83d8-205">ClassName</span></span></li><li><span data-ttu-id="b83d8-206">Priorytet</span><span class="sxs-lookup"><span data-stu-id="b83d8-206">Priority</span></span></li><li><span data-ttu-id="b83d8-207">TestCategory</span><span class="sxs-lookup"><span data-stu-id="b83d8-207">TestCategory</span></span></li></ul> |
| <span data-ttu-id="b83d8-208">xUnit</span><span class="sxs-lookup"><span data-stu-id="b83d8-208">xUnit</span></span>          | <ul><li><span data-ttu-id="b83d8-209">FullyQualifiedName</span><span class="sxs-lookup"><span data-stu-id="b83d8-209">FullyQualifiedName</span></span></li><li><span data-ttu-id="b83d8-210">Nazwa wyświetlana</span><span class="sxs-lookup"><span data-stu-id="b83d8-210">DisplayName</span></span></li><li><span data-ttu-id="b83d8-211">Cechy</span><span class="sxs-lookup"><span data-stu-id="b83d8-211">Traits</span></span></li></ul>                                   |

<span data-ttu-id="b83d8-212">`<operator>` Opisuje relację między właściwości i wartości:</span><span class="sxs-lookup"><span data-stu-id="b83d8-212">The `<operator>` describes the relationship between the property and the value:</span></span>

| <span data-ttu-id="b83d8-213">Operator</span><span class="sxs-lookup"><span data-stu-id="b83d8-213">Operator</span></span> | <span data-ttu-id="b83d8-214">Funkcja</span><span class="sxs-lookup"><span data-stu-id="b83d8-214">Function</span></span>        |
| :------: | --------------- |
| `=`      | <span data-ttu-id="b83d8-215">Dokładne dopasowanie</span><span class="sxs-lookup"><span data-stu-id="b83d8-215">Exact match</span></span>     |
| `!=`     | <span data-ttu-id="b83d8-216">Nie dokładne dopasowanie</span><span class="sxs-lookup"><span data-stu-id="b83d8-216">Not exact match</span></span> |
| `~`      | <span data-ttu-id="b83d8-217">Zawiera</span><span class="sxs-lookup"><span data-stu-id="b83d8-217">Contains</span></span>        |

<span data-ttu-id="b83d8-218">`<value>` jest to ciąg.</span><span class="sxs-lookup"><span data-stu-id="b83d8-218">`<value>` is a string.</span></span> <span data-ttu-id="b83d8-219">Wszystkie wyszukiwania jest rozróżniana wielkość liter.</span><span class="sxs-lookup"><span data-stu-id="b83d8-219">All the lookups are case insensitive.</span></span>

<span data-ttu-id="b83d8-220">Wyrażenie bez `<operator>` jest automatycznie traktowane jako `contains` na `FullyQualifiedName` właściwości (na przykład `dotnet test --filter xyz` jest taka sama jak `dotnet test --filter FullyQualifiedName~xyz`).</span><span class="sxs-lookup"><span data-stu-id="b83d8-220">An expression without an `<operator>` is automatically considered as a `contains` on `FullyQualifiedName` property (for example, `dotnet test --filter xyz` is same as `dotnet test --filter FullyQualifiedName~xyz`).</span></span>

<span data-ttu-id="b83d8-221">Wyrażenia może być łączone z operatorów warunkowych:</span><span class="sxs-lookup"><span data-stu-id="b83d8-221">Expressions can be joined with conditional operators:</span></span>

| <span data-ttu-id="b83d8-222">Operator</span><span class="sxs-lookup"><span data-stu-id="b83d8-222">Operator</span></span>            | <span data-ttu-id="b83d8-223">Funkcja</span><span class="sxs-lookup"><span data-stu-id="b83d8-223">Function</span></span> |
| ------------------- | -------- |
| <code>&#124;</code> | <span data-ttu-id="b83d8-224">LUB</span><span class="sxs-lookup"><span data-stu-id="b83d8-224">OR</span></span>       |
| `&`                 | <span data-ttu-id="b83d8-225">AND</span><span class="sxs-lookup"><span data-stu-id="b83d8-225">AND</span></span>      |

<span data-ttu-id="b83d8-226">Może być częścią wyrażenia w nawiasach przy użyciu operatorów warunkowych (na przykład `(Name~TestMethod1) | (Name~TestMethod2)`).</span><span class="sxs-lookup"><span data-stu-id="b83d8-226">You can enclose expressions in parenthesis when using conditional operators (for example, `(Name~TestMethod1) | (Name~TestMethod2)`).</span></span>

<span data-ttu-id="b83d8-227">Aby uzyskać dodatkowe informacje i przykłady dotyczące korzystania z jednostki selektywne testowanie filtrowania, zobacz [uruchamianie selektywnych testów jednostkowych](../testing/selective-unit-tests.md).</span><span class="sxs-lookup"><span data-stu-id="b83d8-227">For more information and examples on how to use selective unit test filtering, see [Running selective unit tests](../testing/selective-unit-tests.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="b83d8-228">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b83d8-228">See also</span></span>

- [<span data-ttu-id="b83d8-229">Struktury i obiekty docelowe</span><span class="sxs-lookup"><span data-stu-id="b83d8-229">Frameworks and Targets</span></span>](../../standard/frameworks.md)
- [<span data-ttu-id="b83d8-230">Katalog platformy .NET core środowiska uruchomieniowego identyfikator (RID)</span><span class="sxs-lookup"><span data-stu-id="b83d8-230">.NET Core Runtime IDentifier (RID) catalog</span></span>](../rid-catalog.md)
