---
title: polecenie test DotNet — interfejs wiersza polecenia platformy .NET Core
description: Polecenia dotnet test służy do wykonywania testów jednostkowych w danym projekcie.
author: mairaw
ms.author: mairaw
ms.date: 05/29/2018
ms.openlocfilehash: e80ba874ec8d0fbc49858719dc3b9b6e02254c78
ms.sourcegitcommit: ad99773e5e45068ce03b99518008397e1299e0d1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/22/2018
ms.locfileid: "46696459"
---
# <a name="dotnet-test"></a><span data-ttu-id="62d67-103">polecenia DotNet test</span><span class="sxs-lookup"><span data-stu-id="62d67-103">dotnet test</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="62d67-104">Nazwa</span><span class="sxs-lookup"><span data-stu-id="62d67-104">Name</span></span>

<span data-ttu-id="62d67-105">`dotnet test` -Sterownik test .NET służących do wykonywania testów jednostkowych.</span><span class="sxs-lookup"><span data-stu-id="62d67-105">`dotnet test` - .NET test driver used to execute unit tests.</span></span>

## <a name="synopsis"></a><span data-ttu-id="62d67-106">Streszczenie</span><span class="sxs-lookup"><span data-stu-id="62d67-106">Synopsis</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="62d67-107">.NET core 2.1</span><span class="sxs-lookup"><span data-stu-id="62d67-107">.NET Core 2.1</span></span>](#tab/netcore21)

```console
dotnet test [<PROJECT>] [-a|--test-adapter-path] [--blame] [-c|--configuration] [--collect] [-d|--diag] [-f|--framework] [--filter]
    [-l|--logger] [--no-build] [--no-restore] [-o|--output] [-r|--results-directory] [-s|--settings] [-t|--list-tests] [-v|--verbosity]
dotnet test [-h|--help]
```

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="62d67-108">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="62d67-108">.NET Core 2.0</span></span>](#tab/netcore20)

```console
dotnet test [<PROJECT>] [-a|--test-adapter-path] [-c|--configuration] [--collect] [-d|--diag] [-f|--framework] [--filter]
    [-l|--logger] [--no-build] [--no-restore] [-o|--output] [-r|--results-directory] [-s|--settings] [-t|--list-tests] [-v|--verbosity]
dotnet test [-h|--help]
```

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="62d67-109">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="62d67-109">.NET Core 1.x</span></span>](#tab/netcore1x)

```console
dotnet test [<PROJECT>] [-a|--test-adapter-path] [-c|--configuration] [-d|--diag] [-f|--framework] [--filter] [-l|--logger] [--no-build] [-o|--output] [-s|--settings] [-t|--list-tests]  [-v|--verbosity]
dotnet test [-h|--help]
```

---

## <a name="description"></a><span data-ttu-id="62d67-110">Opis</span><span class="sxs-lookup"><span data-stu-id="62d67-110">Description</span></span>

<span data-ttu-id="62d67-111">`dotnet test` Polecenie służy do wykonywania testów jednostkowych w danym projekcie.</span><span class="sxs-lookup"><span data-stu-id="62d67-111">The `dotnet test` command is used to execute unit tests in a given project.</span></span> <span data-ttu-id="62d67-112">`dotnet test` Polecenie uruchamia aplikację konsolową modułu uruchamiającego test, określony dla projektu.</span><span class="sxs-lookup"><span data-stu-id="62d67-112">The `dotnet test` command launches the test runner console application specified for a project.</span></span> <span data-ttu-id="62d67-113">Moduł uruchamiający testy zdefiniowane dla środowiska testów jednostkowych (np. MSTest, NUnit lub xUnit) są wykonywane i zgłasza powodzenie lub niepowodzenie każdego testu.</span><span class="sxs-lookup"><span data-stu-id="62d67-113">The test runner executes the tests defined for a unit test framework (for example, MSTest, NUnit, or xUnit) and reports the success or failure of each test.</span></span> <span data-ttu-id="62d67-114">Jeśli wszystkie testy zakończą się powodzeniem, narzędzia test runner zwraca wartość 0, kod zakończenia; Jeśli dowolny test zakończy się niepowodzeniem, w przeciwnym razie zwraca 1.</span><span class="sxs-lookup"><span data-stu-id="62d67-114">If all tests are successful, the test runner returns 0 as an exit code; otherwise if any test fails, it returns 1.</span></span> <span data-ttu-id="62d67-115">Narzędzie test runner Biblioteka testów jednostkowych jest spakowany jako pakiety NuGet i zostaną przywrócone jako zwykłe zależności projektu.</span><span class="sxs-lookup"><span data-stu-id="62d67-115">The test runner and the unit test library are packaged as NuGet packages and are restored as ordinary dependencies for the project.</span></span>

<span data-ttu-id="62d67-116">Projekty testowe określić modułu uruchamiającego testy przy użyciu zwykłej `<PackageReference>` elementu, jak pokazano w poniższym przykładowym pliku projektu:</span><span class="sxs-lookup"><span data-stu-id="62d67-116">Test projects specify the test runner using an ordinary `<PackageReference>` element, as seen in the following sample project file:</span></span>

[!code-xml[XUnit Basic Template](../../../samples/snippets/csharp/xunit-test/xunit-test.csproj)]

## <a name="arguments"></a><span data-ttu-id="62d67-117">Argumenty</span><span class="sxs-lookup"><span data-stu-id="62d67-117">Arguments</span></span>

`PROJECT`

<span data-ttu-id="62d67-118">Ścieżka do projektu testowego.</span><span class="sxs-lookup"><span data-stu-id="62d67-118">Path to the test project.</span></span> <span data-ttu-id="62d67-119">Jeśli nie zostanie określony, domyślnie bieżącego katalogu.</span><span class="sxs-lookup"><span data-stu-id="62d67-119">If not specified, it defaults to current directory.</span></span>

## <a name="options"></a><span data-ttu-id="62d67-120">Opcje</span><span class="sxs-lookup"><span data-stu-id="62d67-120">Options</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="62d67-121">.NET core 2.1</span><span class="sxs-lookup"><span data-stu-id="62d67-121">.NET Core 2.1</span></span>](#tab/netcore21)

`-a|--test-adapter-path <PATH_TO_ADAPTER>`

<span data-ttu-id="62d67-122">Używa niestandardowych adapterów testowych z określonej ścieżki w przebiegu testu.</span><span class="sxs-lookup"><span data-stu-id="62d67-122">Use the custom test adapters from the specified path in the test run.</span></span>

`--blame`

<span data-ttu-id="62d67-123">Uruchamia testy w trybie polecenia blame.</span><span class="sxs-lookup"><span data-stu-id="62d67-123">Runs the tests in blame mode.</span></span> <span data-ttu-id="62d67-124">Ta opcja jest przydatna polega na wyizolowaniu problematyczne testy, powodując hosta testów ulega awarii.</span><span class="sxs-lookup"><span data-stu-id="62d67-124">This option is helpful in isolating the problematic tests causing test host to crash.</span></span> <span data-ttu-id="62d67-125">Tworzy plik wyjściowy w bieżącym katalogu jako *Sequence.xml* , przechwytuje kolejność wykonywania testów przed awarią.</span><span class="sxs-lookup"><span data-stu-id="62d67-125">It creates an output file in the current directory as *Sequence.xml* that captures the order of tests execution before the crash.</span></span>

`-c|--configuration {Debug|Release}`

<span data-ttu-id="62d67-126">Definiuje konfigurację kompilacji.</span><span class="sxs-lookup"><span data-stu-id="62d67-126">Defines the build configuration.</span></span> <span data-ttu-id="62d67-127">Wartość domyślna to `Debug`, ale konfiguracji projektu można zastąpić to ustawienie SDK domyślne.</span><span class="sxs-lookup"><span data-stu-id="62d67-127">The default value is `Debug`, but your project's configuration could override this default SDK setting.</span></span>

`--collect <DATA_COLLECTOR_FRIENDLY_NAME>`

<span data-ttu-id="62d67-128">Włącza moduł zbierający dane dla przebiegu testu.</span><span class="sxs-lookup"><span data-stu-id="62d67-128">Enables data collector for the test run.</span></span> <span data-ttu-id="62d67-129">Aby uzyskać więcej informacji, zobacz [monitorowanie i analizowanie przebiegu testu](https://aka.ms/vstest-collect).</span><span class="sxs-lookup"><span data-stu-id="62d67-129">For more information, see [Monitor and analyze test run](https://aka.ms/vstest-collect).</span></span>

`-d|--diag <PATH_TO_DIAGNOSTICS_FILE>`

<span data-ttu-id="62d67-130">Włącza tryb diagnostycznych dla testu platformy i zapisu komunikaty diagnostyczne do określonego pliku.</span><span class="sxs-lookup"><span data-stu-id="62d67-130">Enables diagnostic mode for the test platform and write diagnostic messages to the specified file.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="62d67-131">Wyszukuje pliki binarne testu dla określonego [framework](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="62d67-131">Looks for test binaries for a specific [framework](../../standard/frameworks.md).</span></span>

`--filter <EXPRESSION>`

<span data-ttu-id="62d67-132">Filtruje testy w bieżącym projekcie za pomocą podanego wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="62d67-132">Filters out tests in the current project using the given expression.</span></span> <span data-ttu-id="62d67-133">Aby uzyskać więcej informacji, zobacz [szczegóły opcji filtru](#filter-option-details) sekcji.</span><span class="sxs-lookup"><span data-stu-id="62d67-133">For more information, see the [Filter option details](#filter-option-details) section.</span></span> <span data-ttu-id="62d67-134">Aby uzyskać dodatkowe informacje i przykłady dotyczące korzystania z jednostki selektywne testowanie filtrowania, zobacz [uruchamianie selektywnych testów jednostkowych](../testing/selective-unit-tests.md).</span><span class="sxs-lookup"><span data-stu-id="62d67-134">For more information and examples on how to use selective unit test filtering, see [Running selective unit tests](../testing/selective-unit-tests.md).</span></span>

`-h|--help`

<span data-ttu-id="62d67-135">Drukuje krótki pomoc dotyczącą polecenia.</span><span class="sxs-lookup"><span data-stu-id="62d67-135">Prints out a short help for the command.</span></span>

`-l|--logger <LoggerUri/FriendlyName>`

<span data-ttu-id="62d67-136">Określa Rejestrator dla wyników badań.</span><span class="sxs-lookup"><span data-stu-id="62d67-136">Specifies a logger for test results.</span></span>

`--no-build`

<span data-ttu-id="62d67-137">Nie da się skompilować projektu testowego przed jego uruchomieniem.</span><span class="sxs-lookup"><span data-stu-id="62d67-137">Doesn't build the test project before running it.</span></span> <span data-ttu-id="62d67-138">Ustawia ona również niejawne `--no-restore` flagi.</span><span class="sxs-lookup"><span data-stu-id="62d67-138">It also implicit sets the `--no-restore` flag.</span></span>

`--no-restore`

<span data-ttu-id="62d67-139">Przy uruchamianiu polecenia niejawne przywracania nie jest wykonywany.</span><span class="sxs-lookup"><span data-stu-id="62d67-139">Doesn't execute an implicit restore when running the command.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="62d67-140">Katalog, w którym można znaleźć plików binarnych do uruchomienia.</span><span class="sxs-lookup"><span data-stu-id="62d67-140">Directory in which to find the binaries to run.</span></span>

`-r|--results-directory <PATH>`

<span data-ttu-id="62d67-141">Katalog, gdzie wyników testu do umieszczenia.</span><span class="sxs-lookup"><span data-stu-id="62d67-141">The directory where the test results are going to be placed.</span></span> <span data-ttu-id="62d67-142">Jeśli określony katalog nie istnieje, zostanie utworzony.</span><span class="sxs-lookup"><span data-stu-id="62d67-142">If the specified directory doesn't exist, it's created.</span></span>

`-s|--settings <SETTINGS_FILE>`

<span data-ttu-id="62d67-143">Ustawienia używane podczas uruchamiania testów.</span><span class="sxs-lookup"><span data-stu-id="62d67-143">Settings to use when running tests.</span></span>

`-t|--list-tests`

<span data-ttu-id="62d67-144">Listę wszystkich odnalezionych testów w bieżącym projekcie.</span><span class="sxs-lookup"><span data-stu-id="62d67-144">List all of the discovered tests in the current project.</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="62d67-145">Ustawia poziom szczegółowości polecenia.</span><span class="sxs-lookup"><span data-stu-id="62d67-145">Sets the verbosity level of the command.</span></span> <span data-ttu-id="62d67-146">Dozwolone wartości to `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, i `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="62d67-146">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="62d67-147">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="62d67-147">.NET Core 2.0</span></span>](#tab/netcore20)

`-a|--test-adapter-path <PATH_TO_ADAPTER>`

<span data-ttu-id="62d67-148">Używa niestandardowych adapterów testowych z określonej ścieżki w przebiegu testu.</span><span class="sxs-lookup"><span data-stu-id="62d67-148">Use the custom test adapters from the specified path in the test run.</span></span>

`-c|--configuration {Debug|Release}`

<span data-ttu-id="62d67-149">Definiuje konfigurację kompilacji.</span><span class="sxs-lookup"><span data-stu-id="62d67-149">Defines the build configuration.</span></span> <span data-ttu-id="62d67-150">Wartość domyślna to `Debug`, ale konfiguracji projektu można zastąpić to ustawienie SDK domyślne.</span><span class="sxs-lookup"><span data-stu-id="62d67-150">The default value is `Debug`, but your project's configuration could override this default SDK setting.</span></span>

`--collect <DATA_COLLECTOR_FRIENDLY_NAME>`

<span data-ttu-id="62d67-151">Włącza moduł zbierający dane dla przebiegu testu.</span><span class="sxs-lookup"><span data-stu-id="62d67-151">Enables data collector for the test run.</span></span> <span data-ttu-id="62d67-152">Aby uzyskać więcej informacji, zobacz [monitorowanie i analizowanie przebiegu testu](https://aka.ms/vstest-collect).</span><span class="sxs-lookup"><span data-stu-id="62d67-152">For more information, see [Monitor and analyze test run](https://aka.ms/vstest-collect).</span></span>

`-d|--diag <PATH_TO_DIAGNOSTICS_FILE>`

<span data-ttu-id="62d67-153">Włącza tryb diagnostycznych dla testu platformy i zapisu komunikaty diagnostyczne do określonego pliku.</span><span class="sxs-lookup"><span data-stu-id="62d67-153">Enables diagnostic mode for the test platform and write diagnostic messages to the specified file.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="62d67-154">Wyszukuje pliki binarne testu dla określonego [framework](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="62d67-154">Looks for test binaries for a specific [framework](../../standard/frameworks.md).</span></span>

`--filter <EXPRESSION>`

<span data-ttu-id="62d67-155">Filtruje testy w bieżącym projekcie za pomocą podanego wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="62d67-155">Filters out tests in the current project using the given expression.</span></span> <span data-ttu-id="62d67-156">Aby uzyskać więcej informacji, zobacz [szczegóły opcji filtru](#filter-option-details) sekcji.</span><span class="sxs-lookup"><span data-stu-id="62d67-156">For more information, see the [Filter option details](#filter-option-details) section.</span></span> <span data-ttu-id="62d67-157">Aby uzyskać dodatkowe informacje i przykłady dotyczące korzystania z jednostki selektywne testowanie filtrowania, zobacz [uruchamianie selektywnych testów jednostkowych](../testing/selective-unit-tests.md).</span><span class="sxs-lookup"><span data-stu-id="62d67-157">For more information and examples on how to use selective unit test filtering, see [Running selective unit tests](../testing/selective-unit-tests.md).</span></span>

`-h|--help`

<span data-ttu-id="62d67-158">Drukuje krótki pomoc dotyczącą polecenia.</span><span class="sxs-lookup"><span data-stu-id="62d67-158">Prints out a short help for the command.</span></span>

`-l|--logger <LoggerUri/FriendlyName>`

<span data-ttu-id="62d67-159">Określa Rejestrator dla wyników badań.</span><span class="sxs-lookup"><span data-stu-id="62d67-159">Specifies a logger for test results.</span></span>

`--no-build`

<span data-ttu-id="62d67-160">Nie da się skompilować projektu testowego przed jego uruchomieniem.</span><span class="sxs-lookup"><span data-stu-id="62d67-160">Doesn't build the test project before running it.</span></span> <span data-ttu-id="62d67-161">Ustawia ona również niejawne `--no-restore` flagi.</span><span class="sxs-lookup"><span data-stu-id="62d67-161">It also implicit sets the `--no-restore` flag.</span></span>

`--no-restore`

<span data-ttu-id="62d67-162">Przy uruchamianiu polecenia niejawne przywracania nie jest wykonywany.</span><span class="sxs-lookup"><span data-stu-id="62d67-162">Doesn't execute an implicit restore when running the command.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="62d67-163">Katalog, w którym można znaleźć plików binarnych do uruchomienia.</span><span class="sxs-lookup"><span data-stu-id="62d67-163">Directory in which to find the binaries to run.</span></span>

`-r|--results-directory <PATH>`

<span data-ttu-id="62d67-164">Katalog, gdzie wyników testu do umieszczenia.</span><span class="sxs-lookup"><span data-stu-id="62d67-164">The directory where the test results are going to be placed.</span></span> <span data-ttu-id="62d67-165">Jeśli określony katalog nie istnieje, zostanie utworzony.</span><span class="sxs-lookup"><span data-stu-id="62d67-165">If the specified directory doesn't exist, it's created.</span></span>

`-s|--settings <SETTINGS_FILE>`

<span data-ttu-id="62d67-166">Ustawienia używane podczas uruchamiania testów.</span><span class="sxs-lookup"><span data-stu-id="62d67-166">Settings to use when running tests.</span></span>

`-t|--list-tests`

<span data-ttu-id="62d67-167">Listę wszystkich odnalezionych testów w bieżącym projekcie.</span><span class="sxs-lookup"><span data-stu-id="62d67-167">List all of the discovered tests in the current project.</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="62d67-168">Ustawia poziom szczegółowości polecenia.</span><span class="sxs-lookup"><span data-stu-id="62d67-168">Sets the verbosity level of the command.</span></span> <span data-ttu-id="62d67-169">Dozwolone wartości to `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, i `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="62d67-169">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="62d67-170">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="62d67-170">.NET Core 1.x</span></span>](#tab/netcore1x)

`-a|--test-adapter-path <PATH_TO_ADAPTER>`

<span data-ttu-id="62d67-171">Używa niestandardowych adapterów testowych z określonej ścieżki w przebiegu testu.</span><span class="sxs-lookup"><span data-stu-id="62d67-171">Use the custom test adapters from the specified path in the test run.</span></span>

`-c|--configuration {Debug|Release}`

<span data-ttu-id="62d67-172">Definiuje konfigurację kompilacji.</span><span class="sxs-lookup"><span data-stu-id="62d67-172">Defines the build configuration.</span></span> <span data-ttu-id="62d67-173">Wartość domyślna to `Debug`, ale konfiguracji projektu można zastąpić to ustawienie SDK domyślne.</span><span class="sxs-lookup"><span data-stu-id="62d67-173">The default value is `Debug`, but your project's configuration could override this default SDK setting.</span></span>

`-d|--diag <PATH_TO_DIAGNOSTICS_FILE>`

<span data-ttu-id="62d67-174">Włącza tryb diagnostycznych dla testu platformy i zapisu komunikaty diagnostyczne do określonego pliku.</span><span class="sxs-lookup"><span data-stu-id="62d67-174">Enables diagnostic mode for the test platform and write diagnostic messages to the specified file.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="62d67-175">Wyszukuje pliki binarne testu dla określonego [framework](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="62d67-175">Looks for test binaries for a specific [framework](../../standard/frameworks.md).</span></span>

`--filter <EXPRESSION>`

<span data-ttu-id="62d67-176">Filtruje testy w bieżącym projekcie za pomocą podanego wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="62d67-176">Filters out tests in the current project using the given expression.</span></span> <span data-ttu-id="62d67-177">Aby uzyskać więcej informacji, zobacz [szczegóły opcji filtru](#filter-option-details) sekcji.</span><span class="sxs-lookup"><span data-stu-id="62d67-177">For more information, see the [Filter option details](#filter-option-details) section.</span></span> <span data-ttu-id="62d67-178">Aby uzyskać dodatkowe informacje i przykłady dotyczące korzystania z jednostki selektywne testowanie filtrowania, zobacz [uruchamianie selektywnych testów jednostkowych](../testing/selective-unit-tests.md).</span><span class="sxs-lookup"><span data-stu-id="62d67-178">For more information and examples on how to use selective unit test filtering, see [Running selective unit tests](../testing/selective-unit-tests.md).</span></span>

`-h|--help`

<span data-ttu-id="62d67-179">Drukuje krótki pomoc dotyczącą polecenia.</span><span class="sxs-lookup"><span data-stu-id="62d67-179">Prints out a short help for the command.</span></span>

`-l|--logger <LoggerUri/FriendlyName>`

<span data-ttu-id="62d67-180">Określa Rejestrator dla wyników badań.</span><span class="sxs-lookup"><span data-stu-id="62d67-180">Specifies a logger for test results.</span></span>

`--no-build`

<span data-ttu-id="62d67-181">Nie da się skompilować projektu testowego przed jego uruchomieniem.</span><span class="sxs-lookup"><span data-stu-id="62d67-181">Doesn't build the test project before running it.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="62d67-182">Katalog, w którym można znaleźć plików binarnych do uruchomienia.</span><span class="sxs-lookup"><span data-stu-id="62d67-182">Directory in which to find the binaries to run.</span></span>

`-s|--settings <SETTINGS_FILE>`

<span data-ttu-id="62d67-183">Ustawienia używane podczas uruchamiania testów.</span><span class="sxs-lookup"><span data-stu-id="62d67-183">Settings to use when running tests.</span></span>

`-t|--list-tests`

<span data-ttu-id="62d67-184">Listę wszystkich odnalezionych testów w bieżącym projekcie.</span><span class="sxs-lookup"><span data-stu-id="62d67-184">List all of the discovered tests in the current project.</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="62d67-185">Ustawia poziom szczegółowości polecenia.</span><span class="sxs-lookup"><span data-stu-id="62d67-185">Sets the verbosity level of the command.</span></span> <span data-ttu-id="62d67-186">Dozwolone wartości to `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, i `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="62d67-186">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

---

## <a name="examples"></a><span data-ttu-id="62d67-187">Przykłady</span><span class="sxs-lookup"><span data-stu-id="62d67-187">Examples</span></span>

<span data-ttu-id="62d67-188">Uruchom testy w projekcie w bieżącym katalogu:</span><span class="sxs-lookup"><span data-stu-id="62d67-188">Run the tests in the project in the current directory:</span></span>

`dotnet test`

<span data-ttu-id="62d67-189">Uruchom testy `test1` projektu:</span><span class="sxs-lookup"><span data-stu-id="62d67-189">Run the tests in the `test1` project:</span></span>

`dotnet test ~/projects/test1/test1.csproj`

<span data-ttu-id="62d67-190">Uruchom testy w projekcie w bieżącym katalogu i wygenerować plik wyników testu w formacie trx:</span><span class="sxs-lookup"><span data-stu-id="62d67-190">Run the tests in the project in the current directory and generate a test results file in the trx format:</span></span>

`dotnet test --logger:trx`

## <a name="filter-option-details"></a><span data-ttu-id="62d67-191">Szczegóły opcji filtru</span><span class="sxs-lookup"><span data-stu-id="62d67-191">Filter option details</span></span>

`--filter <EXPRESSION>`

<span data-ttu-id="62d67-192">`<Expression>` ma format `<property><operator><value>[|&<Expression>]`.</span><span class="sxs-lookup"><span data-stu-id="62d67-192">`<Expression>` has the format `<property><operator><value>[|&<Expression>]`.</span></span>

<span data-ttu-id="62d67-193">`<property>` jest to atrybut `Test Case`.</span><span class="sxs-lookup"><span data-stu-id="62d67-193">`<property>` is an attribute of the `Test Case`.</span></span> <span data-ttu-id="62d67-194">Poniżej przedstawiono właściwości obsługiwanych przez platform testów jednostkowych innych popularnych:</span><span class="sxs-lookup"><span data-stu-id="62d67-194">The following are the properties supported by popular unit test frameworks:</span></span>

| <span data-ttu-id="62d67-195">Struktury testowej</span><span class="sxs-lookup"><span data-stu-id="62d67-195">Test Framework</span></span> | <span data-ttu-id="62d67-196">Obsługiwanych właściwości</span><span class="sxs-lookup"><span data-stu-id="62d67-196">Supported properties</span></span>                                                                                      |
| -------------- | --------------------------------------------------------------------------------------------------------- |
| <span data-ttu-id="62d67-197">MSTest</span><span class="sxs-lookup"><span data-stu-id="62d67-197">MSTest</span></span>         | <ul><li><span data-ttu-id="62d67-198">FullyQualifiedName</span><span class="sxs-lookup"><span data-stu-id="62d67-198">FullyQualifiedName</span></span></li><li><span data-ttu-id="62d67-199">Nazwa</span><span class="sxs-lookup"><span data-stu-id="62d67-199">Name</span></span></li><li><span data-ttu-id="62d67-200">className</span><span class="sxs-lookup"><span data-stu-id="62d67-200">ClassName</span></span></li><li><span data-ttu-id="62d67-201">Priorytet</span><span class="sxs-lookup"><span data-stu-id="62d67-201">Priority</span></span></li><li><span data-ttu-id="62d67-202">TestCategory</span><span class="sxs-lookup"><span data-stu-id="62d67-202">TestCategory</span></span></li></ul> |
| <span data-ttu-id="62d67-203">xUnit</span><span class="sxs-lookup"><span data-stu-id="62d67-203">xUnit</span></span>          | <ul><li><span data-ttu-id="62d67-204">FullyQualifiedName</span><span class="sxs-lookup"><span data-stu-id="62d67-204">FullyQualifiedName</span></span></li><li><span data-ttu-id="62d67-205">Nazwa wyświetlana</span><span class="sxs-lookup"><span data-stu-id="62d67-205">DisplayName</span></span></li><li><span data-ttu-id="62d67-206">Cechy</span><span class="sxs-lookup"><span data-stu-id="62d67-206">Traits</span></span></li></ul>                                   |

<span data-ttu-id="62d67-207">`<operator>` Opisuje relację między właściwości i wartości:</span><span class="sxs-lookup"><span data-stu-id="62d67-207">The `<operator>` describes the relationship between the property and the value:</span></span>

| <span data-ttu-id="62d67-208">Operator</span><span class="sxs-lookup"><span data-stu-id="62d67-208">Operator</span></span> | <span data-ttu-id="62d67-209">Funkcja</span><span class="sxs-lookup"><span data-stu-id="62d67-209">Function</span></span>        |
| :------: | --------------- |
| `=`      | <span data-ttu-id="62d67-210">Dokładne dopasowanie</span><span class="sxs-lookup"><span data-stu-id="62d67-210">Exact match</span></span>     |
| `!=`     | <span data-ttu-id="62d67-211">Nie dokładne dopasowanie</span><span class="sxs-lookup"><span data-stu-id="62d67-211">Not exact match</span></span> |
| `~`      | <span data-ttu-id="62d67-212">Zawiera</span><span class="sxs-lookup"><span data-stu-id="62d67-212">Contains</span></span>        |

<span data-ttu-id="62d67-213">`<value>` jest to ciąg.</span><span class="sxs-lookup"><span data-stu-id="62d67-213">`<value>` is a string.</span></span> <span data-ttu-id="62d67-214">Wszystkie wyszukiwania jest rozróżniana wielkość liter.</span><span class="sxs-lookup"><span data-stu-id="62d67-214">All the lookups are case insensitive.</span></span>

<span data-ttu-id="62d67-215">Wyrażenie bez `<operator>` jest automatycznie traktowane jako `contains` na `FullyQualifiedName` właściwości (na przykład `dotnet test --filter xyz` jest taka sama jak `dotnet test --filter FullyQualifiedName~xyz`).</span><span class="sxs-lookup"><span data-stu-id="62d67-215">An expression without an `<operator>` is automatically considered as a `contains` on `FullyQualifiedName` property (for example, `dotnet test --filter xyz` is same as `dotnet test --filter FullyQualifiedName~xyz`).</span></span>

<span data-ttu-id="62d67-216">Wyrażenia może być łączone z operatorów warunkowych:</span><span class="sxs-lookup"><span data-stu-id="62d67-216">Expressions can be joined with conditional operators:</span></span>

| <span data-ttu-id="62d67-217">Operator</span><span class="sxs-lookup"><span data-stu-id="62d67-217">Operator</span></span>            | <span data-ttu-id="62d67-218">Funkcja</span><span class="sxs-lookup"><span data-stu-id="62d67-218">Function</span></span> |
| ------------------- | -------- |
| <code>&#124;</code> | <span data-ttu-id="62d67-219">LUB</span><span class="sxs-lookup"><span data-stu-id="62d67-219">OR</span></span>       |
| `&`                 | <span data-ttu-id="62d67-220">AND</span><span class="sxs-lookup"><span data-stu-id="62d67-220">AND</span></span>      |

<span data-ttu-id="62d67-221">Może być częścią wyrażenia w nawiasach przy użyciu operatorów warunkowych (na przykład `(Name~TestMethod1) | (Name~TestMethod2)`).</span><span class="sxs-lookup"><span data-stu-id="62d67-221">You can enclose expressions in parenthesis when using conditional operators (for example, `(Name~TestMethod1) | (Name~TestMethod2)`).</span></span>

<span data-ttu-id="62d67-222">Aby uzyskać dodatkowe informacje i przykłady dotyczące korzystania z jednostki selektywne testowanie filtrowania, zobacz [uruchamianie selektywnych testów jednostkowych](../testing/selective-unit-tests.md).</span><span class="sxs-lookup"><span data-stu-id="62d67-222">For more information and examples on how to use selective unit test filtering, see [Running selective unit tests](../testing/selective-unit-tests.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="62d67-223">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="62d67-223">See also</span></span>

* [<span data-ttu-id="62d67-224">Struktury i obiekty docelowe</span><span class="sxs-lookup"><span data-stu-id="62d67-224">Frameworks and Targets</span></span>](../../standard/frameworks.md)  
* [<span data-ttu-id="62d67-225">Katalog platformy .NET core środowiska uruchomieniowego identyfikator (RID)</span><span class="sxs-lookup"><span data-stu-id="62d67-225">.NET Core Runtime IDentifier (RID) catalog</span></span>](../rid-catalog.md)
