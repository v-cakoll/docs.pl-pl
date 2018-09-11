---
title: polecenie test DotNet — interfejs wiersza polecenia platformy .NET Core
description: Polecenia dotnet test służy do wykonywania testów jednostkowych w danym projekcie.
author: mairaw
ms.author: mairaw
ms.date: 05/29/2018
ms.openlocfilehash: 7946196b27489870da1c16b15cbf5f078ae89c61
ms.sourcegitcommit: 67de6cb5dd66a19f2180ba7e4d7aecc697f8a963
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/10/2018
ms.locfileid: "44339607"
---
# <a name="dotnet-test"></a><span data-ttu-id="4b895-103">polecenia DotNet test</span><span class="sxs-lookup"><span data-stu-id="4b895-103">dotnet test</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="4b895-104">Nazwa</span><span class="sxs-lookup"><span data-stu-id="4b895-104">Name</span></span>

<span data-ttu-id="4b895-105">`dotnet test` -Sterownik test .NET służących do wykonywania testów jednostkowych.</span><span class="sxs-lookup"><span data-stu-id="4b895-105">`dotnet test` - .NET test driver used to execute unit tests.</span></span>

## <a name="synopsis"></a><span data-ttu-id="4b895-106">Streszczenie</span><span class="sxs-lookup"><span data-stu-id="4b895-106">Synopsis</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="4b895-107">.NET core 2.1</span><span class="sxs-lookup"><span data-stu-id="4b895-107">.NET Core 2.1</span></span>](#tab/netcore21)

```console
dotnet test [<PROJECT>] [-a|--test-adapter-path] [--blame] [-c|--configuration] [--collect] [-d|--diag] [-f|--framework] [--filter]
    [-l|--logger] [--no-build] [--no-restore] [-o|--output] [-r|--results-directory] [-s|--settings] [-t|--list-tests] [-v|--verbosity]
dotnet test [-h|--help]
```

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="4b895-108">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="4b895-108">.NET Core 2.0</span></span>](#tab/netcore20)

```console
dotnet test [<PROJECT>] [-a|--test-adapter-path] [-c|--configuration] [--collect] [-d|--diag] [-f|--framework] [--filter]
    [-l|--logger] [--no-build] [--no-restore] [-o|--output] [-r|--results-directory] [-s|--settings] [-t|--list-tests] [-v|--verbosity]
dotnet test [-h|--help]
```

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="4b895-109">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="4b895-109">.NET Core 1.x</span></span>](#tab/netcore1x)

```console
dotnet test [<PROJECT>] [-a|--test-adapter-path] [-c|--configuration] [-d|--diag] [-f|--framework] [--filter] [-l|--logger] [--no-build] [-o|--output] [-s|--settings] [-t|--list-tests]  [-v|--verbosity]
dotnet test [-h|--help]
```

---

## <a name="description"></a><span data-ttu-id="4b895-110">Opis</span><span class="sxs-lookup"><span data-stu-id="4b895-110">Description</span></span>

<span data-ttu-id="4b895-111">`dotnet test` Polecenie służy do wykonywania testów jednostkowych w danym projekcie.</span><span class="sxs-lookup"><span data-stu-id="4b895-111">The `dotnet test` command is used to execute unit tests in a given project.</span></span> <span data-ttu-id="4b895-112">`dotnet test` Polecenie uruchamia aplikację konsolową modułu uruchamiającego test, określony dla projektu.</span><span class="sxs-lookup"><span data-stu-id="4b895-112">The `dotnet test` command launches the test runner console application specified for a project.</span></span> <span data-ttu-id="4b895-113">Moduł uruchamiający testy zdefiniowane dla środowiska testów jednostkowych (np. MSTest, NUnit lub xUnit) są wykonywane i zgłasza powodzenie lub niepowodzenie każdego testu.</span><span class="sxs-lookup"><span data-stu-id="4b895-113">The test runner executes the tests defined for a unit test framework (for example, MSTest, NUnit, or xUnit) and reports the success or failure of each test.</span></span> <span data-ttu-id="4b895-114">Narzędzie test runner Biblioteka testów jednostkowych jest spakowany jako pakiety NuGet i zostaną przywrócone jako zwykłe zależności projektu.</span><span class="sxs-lookup"><span data-stu-id="4b895-114">The test runner and the unit test library are packaged as NuGet packages and are restored as ordinary dependencies for the project.</span></span>

<span data-ttu-id="4b895-115">Projekty testowe określić modułu uruchamiającego testy przy użyciu zwykłej `<PackageReference>` elementu, jak pokazano w poniższym przykładowym pliku projektu:</span><span class="sxs-lookup"><span data-stu-id="4b895-115">Test projects specify the test runner using an ordinary `<PackageReference>` element, as seen in the following sample project file:</span></span>

[!code-xml[XUnit Basic Template](../../../samples/snippets/csharp/xunit-test/xunit-test.csproj)]

## <a name="arguments"></a><span data-ttu-id="4b895-116">Argumenty</span><span class="sxs-lookup"><span data-stu-id="4b895-116">Arguments</span></span>

`PROJECT`

<span data-ttu-id="4b895-117">Ścieżka do projektu testowego.</span><span class="sxs-lookup"><span data-stu-id="4b895-117">Path to the test project.</span></span> <span data-ttu-id="4b895-118">Jeśli nie zostanie określony, domyślnie bieżącego katalogu.</span><span class="sxs-lookup"><span data-stu-id="4b895-118">If not specified, it defaults to current directory.</span></span>

## <a name="options"></a><span data-ttu-id="4b895-119">Opcje</span><span class="sxs-lookup"><span data-stu-id="4b895-119">Options</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="4b895-120">.NET core 2.1</span><span class="sxs-lookup"><span data-stu-id="4b895-120">.NET Core 2.1</span></span>](#tab/netcore21)

`-a|--test-adapter-path <PATH_TO_ADAPTER>`

<span data-ttu-id="4b895-121">Używa niestandardowych adapterów testowych z określonej ścieżki w przebiegu testu.</span><span class="sxs-lookup"><span data-stu-id="4b895-121">Use the custom test adapters from the specified path in the test run.</span></span>

`--blame`

<span data-ttu-id="4b895-122">Uruchamia testy w trybie polecenia blame.</span><span class="sxs-lookup"><span data-stu-id="4b895-122">Runs the tests in blame mode.</span></span> <span data-ttu-id="4b895-123">Ta opcja jest przydatna polega na wyizolowaniu problematyczne testy, powodując hosta testów ulega awarii.</span><span class="sxs-lookup"><span data-stu-id="4b895-123">This option is helpful in isolating the problematic tests causing test host to crash.</span></span> <span data-ttu-id="4b895-124">Tworzy plik wyjściowy w bieżącym katalogu jako *Sequence.xml* , przechwytuje kolejność wykonywania testów przed awarią.</span><span class="sxs-lookup"><span data-stu-id="4b895-124">It creates an output file in the current directory as *Sequence.xml* that captures the order of tests execution before the crash.</span></span>

`-c|--configuration {Debug|Release}`

<span data-ttu-id="4b895-125">Definiuje konfigurację kompilacji.</span><span class="sxs-lookup"><span data-stu-id="4b895-125">Defines the build configuration.</span></span> <span data-ttu-id="4b895-126">Wartość domyślna to `Debug`, ale konfiguracji projektu można zastąpić to ustawienie SDK domyślne.</span><span class="sxs-lookup"><span data-stu-id="4b895-126">The default value is `Debug`, but your project's configuration could override this default SDK setting.</span></span>

`--collect <DATA_COLLECTOR_FRIENDLY_NAME>`

<span data-ttu-id="4b895-127">Włącza moduł zbierający dane dla przebiegu testu.</span><span class="sxs-lookup"><span data-stu-id="4b895-127">Enables data collector for the test run.</span></span> <span data-ttu-id="4b895-128">Aby uzyskać więcej informacji, zobacz [monitorowanie i analizowanie przebiegu testu](https://aka.ms/vstest-collect).</span><span class="sxs-lookup"><span data-stu-id="4b895-128">For more information, see [Monitor and analyze test run](https://aka.ms/vstest-collect).</span></span>

`-d|--diag <PATH_TO_DIAGNOSTICS_FILE>`

<span data-ttu-id="4b895-129">Włącza tryb diagnostycznych dla testu platformy i zapisu komunikaty diagnostyczne do określonego pliku.</span><span class="sxs-lookup"><span data-stu-id="4b895-129">Enables diagnostic mode for the test platform and write diagnostic messages to the specified file.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="4b895-130">Wyszukuje pliki binarne testu dla określonego [framework](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="4b895-130">Looks for test binaries for a specific [framework](../../standard/frameworks.md).</span></span>

`--filter <EXPRESSION>`

<span data-ttu-id="4b895-131">Filtruje testy w bieżącym projekcie za pomocą podanego wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="4b895-131">Filters out tests in the current project using the given expression.</span></span> <span data-ttu-id="4b895-132">Aby uzyskać więcej informacji, zobacz [szczegóły opcji filtru](#filter-option-details) sekcji.</span><span class="sxs-lookup"><span data-stu-id="4b895-132">For more information, see the [Filter option details](#filter-option-details) section.</span></span> <span data-ttu-id="4b895-133">Aby uzyskać dodatkowe informacje i przykłady dotyczące korzystania z jednostki selektywne testowanie filtrowania, zobacz [uruchamianie selektywnych testów jednostkowych](../testing/selective-unit-tests.md).</span><span class="sxs-lookup"><span data-stu-id="4b895-133">For more information and examples on how to use selective unit test filtering, see [Running selective unit tests](../testing/selective-unit-tests.md).</span></span>

`-h|--help`

<span data-ttu-id="4b895-134">Drukuje krótki pomoc dotyczącą polecenia.</span><span class="sxs-lookup"><span data-stu-id="4b895-134">Prints out a short help for the command.</span></span>

`-l|--logger <LoggerUri/FriendlyName>`

<span data-ttu-id="4b895-135">Określa Rejestrator dla wyników badań.</span><span class="sxs-lookup"><span data-stu-id="4b895-135">Specifies a logger for test results.</span></span>

`--no-build`

<span data-ttu-id="4b895-136">Nie da się skompilować projektu testowego przed jego uruchomieniem.</span><span class="sxs-lookup"><span data-stu-id="4b895-136">Doesn't build the test project before running it.</span></span> <span data-ttu-id="4b895-137">Ustawia ona również niejawne `--no-restore` flagi.</span><span class="sxs-lookup"><span data-stu-id="4b895-137">It also implicit sets the `--no-restore` flag.</span></span>

`--no-restore`

<span data-ttu-id="4b895-138">Przy uruchamianiu polecenia niejawne przywracania nie jest wykonywany.</span><span class="sxs-lookup"><span data-stu-id="4b895-138">Doesn't execute an implicit restore when running the command.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="4b895-139">Katalog, w którym można znaleźć plików binarnych do uruchomienia.</span><span class="sxs-lookup"><span data-stu-id="4b895-139">Directory in which to find the binaries to run.</span></span>

`-r|--results-directory <PATH>`

<span data-ttu-id="4b895-140">Katalog, gdzie wyników testu do umieszczenia.</span><span class="sxs-lookup"><span data-stu-id="4b895-140">The directory where the test results are going to be placed.</span></span> <span data-ttu-id="4b895-141">Jeśli określony katalog nie istnieje, zostanie utworzony.</span><span class="sxs-lookup"><span data-stu-id="4b895-141">If the specified directory doesn't exist, it's created.</span></span>

`-s|--settings <SETTINGS_FILE>`

<span data-ttu-id="4b895-142">Ustawienia używane podczas uruchamiania testów.</span><span class="sxs-lookup"><span data-stu-id="4b895-142">Settings to use when running tests.</span></span>

`-t|--list-tests`

<span data-ttu-id="4b895-143">Listę wszystkich odnalezionych testów w bieżącym projekcie.</span><span class="sxs-lookup"><span data-stu-id="4b895-143">List all of the discovered tests in the current project.</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="4b895-144">Ustawia poziom szczegółowości polecenia.</span><span class="sxs-lookup"><span data-stu-id="4b895-144">Sets the verbosity level of the command.</span></span> <span data-ttu-id="4b895-145">Dozwolone wartości to `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, i `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="4b895-145">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="4b895-146">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="4b895-146">.NET Core 2.0</span></span>](#tab/netcore20)

`-a|--test-adapter-path <PATH_TO_ADAPTER>`

<span data-ttu-id="4b895-147">Używa niestandardowych adapterów testowych z określonej ścieżki w przebiegu testu.</span><span class="sxs-lookup"><span data-stu-id="4b895-147">Use the custom test adapters from the specified path in the test run.</span></span>

`-c|--configuration {Debug|Release}`

<span data-ttu-id="4b895-148">Definiuje konfigurację kompilacji.</span><span class="sxs-lookup"><span data-stu-id="4b895-148">Defines the build configuration.</span></span> <span data-ttu-id="4b895-149">Wartość domyślna to `Debug`, ale konfiguracji projektu można zastąpić to ustawienie SDK domyślne.</span><span class="sxs-lookup"><span data-stu-id="4b895-149">The default value is `Debug`, but your project's configuration could override this default SDK setting.</span></span>

`--collect <DATA_COLLECTOR_FRIENDLY_NAME>`

<span data-ttu-id="4b895-150">Włącza moduł zbierający dane dla przebiegu testu.</span><span class="sxs-lookup"><span data-stu-id="4b895-150">Enables data collector for the test run.</span></span> <span data-ttu-id="4b895-151">Aby uzyskać więcej informacji, zobacz [monitorowanie i analizowanie przebiegu testu](https://aka.ms/vstest-collect).</span><span class="sxs-lookup"><span data-stu-id="4b895-151">For more information, see [Monitor and analyze test run](https://aka.ms/vstest-collect).</span></span>

`-d|--diag <PATH_TO_DIAGNOSTICS_FILE>`

<span data-ttu-id="4b895-152">Włącza tryb diagnostycznych dla testu platformy i zapisu komunikaty diagnostyczne do określonego pliku.</span><span class="sxs-lookup"><span data-stu-id="4b895-152">Enables diagnostic mode for the test platform and write diagnostic messages to the specified file.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="4b895-153">Wyszukuje pliki binarne testu dla określonego [framework](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="4b895-153">Looks for test binaries for a specific [framework](../../standard/frameworks.md).</span></span>

`--filter <EXPRESSION>`

<span data-ttu-id="4b895-154">Filtruje testy w bieżącym projekcie za pomocą podanego wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="4b895-154">Filters out tests in the current project using the given expression.</span></span> <span data-ttu-id="4b895-155">Aby uzyskać więcej informacji, zobacz [szczegóły opcji filtru](#filter-option-details) sekcji.</span><span class="sxs-lookup"><span data-stu-id="4b895-155">For more information, see the [Filter option details](#filter-option-details) section.</span></span> <span data-ttu-id="4b895-156">Aby uzyskać dodatkowe informacje i przykłady dotyczące korzystania z jednostki selektywne testowanie filtrowania, zobacz [uruchamianie selektywnych testów jednostkowych](../testing/selective-unit-tests.md).</span><span class="sxs-lookup"><span data-stu-id="4b895-156">For more information and examples on how to use selective unit test filtering, see [Running selective unit tests](../testing/selective-unit-tests.md).</span></span>

`-h|--help`

<span data-ttu-id="4b895-157">Drukuje krótki pomoc dotyczącą polecenia.</span><span class="sxs-lookup"><span data-stu-id="4b895-157">Prints out a short help for the command.</span></span>

`-l|--logger <LoggerUri/FriendlyName>`

<span data-ttu-id="4b895-158">Określa Rejestrator dla wyników badań.</span><span class="sxs-lookup"><span data-stu-id="4b895-158">Specifies a logger for test results.</span></span>

`--no-build`

<span data-ttu-id="4b895-159">Nie da się skompilować projektu testowego przed jego uruchomieniem.</span><span class="sxs-lookup"><span data-stu-id="4b895-159">Doesn't build the test project before running it.</span></span> <span data-ttu-id="4b895-160">Ustawia ona również niejawne `--no-restore` flagi.</span><span class="sxs-lookup"><span data-stu-id="4b895-160">It also implicit sets the `--no-restore` flag.</span></span>

`--no-restore`

<span data-ttu-id="4b895-161">Przy uruchamianiu polecenia niejawne przywracania nie jest wykonywany.</span><span class="sxs-lookup"><span data-stu-id="4b895-161">Doesn't execute an implicit restore when running the command.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="4b895-162">Katalog, w którym można znaleźć plików binarnych do uruchomienia.</span><span class="sxs-lookup"><span data-stu-id="4b895-162">Directory in which to find the binaries to run.</span></span>

`-r|--results-directory <PATH>`

<span data-ttu-id="4b895-163">Katalog, gdzie wyników testu do umieszczenia.</span><span class="sxs-lookup"><span data-stu-id="4b895-163">The directory where the test results are going to be placed.</span></span> <span data-ttu-id="4b895-164">Jeśli określony katalog nie istnieje, zostanie utworzony.</span><span class="sxs-lookup"><span data-stu-id="4b895-164">If the specified directory doesn't exist, it's created.</span></span>

`-s|--settings <SETTINGS_FILE>`

<span data-ttu-id="4b895-165">Ustawienia używane podczas uruchamiania testów.</span><span class="sxs-lookup"><span data-stu-id="4b895-165">Settings to use when running tests.</span></span>

`-t|--list-tests`

<span data-ttu-id="4b895-166">Listę wszystkich odnalezionych testów w bieżącym projekcie.</span><span class="sxs-lookup"><span data-stu-id="4b895-166">List all of the discovered tests in the current project.</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="4b895-167">Ustawia poziom szczegółowości polecenia.</span><span class="sxs-lookup"><span data-stu-id="4b895-167">Sets the verbosity level of the command.</span></span> <span data-ttu-id="4b895-168">Dozwolone wartości to `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, i `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="4b895-168">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="4b895-169">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="4b895-169">.NET Core 1.x</span></span>](#tab/netcore1x)

`-a|--test-adapter-path <PATH_TO_ADAPTER>`

<span data-ttu-id="4b895-170">Używa niestandardowych adapterów testowych z określonej ścieżki w przebiegu testu.</span><span class="sxs-lookup"><span data-stu-id="4b895-170">Use the custom test adapters from the specified path in the test run.</span></span>

`-c|--configuration {Debug|Release}`

<span data-ttu-id="4b895-171">Definiuje konfigurację kompilacji.</span><span class="sxs-lookup"><span data-stu-id="4b895-171">Defines the build configuration.</span></span> <span data-ttu-id="4b895-172">Wartość domyślna to `Debug`, ale konfiguracji projektu można zastąpić to ustawienie SDK domyślne.</span><span class="sxs-lookup"><span data-stu-id="4b895-172">The default value is `Debug`, but your project's configuration could override this default SDK setting.</span></span>

`-d|--diag <PATH_TO_DIAGNOSTICS_FILE>`

<span data-ttu-id="4b895-173">Włącza tryb diagnostycznych dla testu platformy i zapisu komunikaty diagnostyczne do określonego pliku.</span><span class="sxs-lookup"><span data-stu-id="4b895-173">Enables diagnostic mode for the test platform and write diagnostic messages to the specified file.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="4b895-174">Wyszukuje pliki binarne testu dla określonego [framework](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="4b895-174">Looks for test binaries for a specific [framework](../../standard/frameworks.md).</span></span>

`--filter <EXPRESSION>`

<span data-ttu-id="4b895-175">Filtruje testy w bieżącym projekcie za pomocą podanego wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="4b895-175">Filters out tests in the current project using the given expression.</span></span> <span data-ttu-id="4b895-176">Aby uzyskać więcej informacji, zobacz [szczegóły opcji filtru](#filter-option-details) sekcji.</span><span class="sxs-lookup"><span data-stu-id="4b895-176">For more information, see the [Filter option details](#filter-option-details) section.</span></span> <span data-ttu-id="4b895-177">Aby uzyskać dodatkowe informacje i przykłady dotyczące korzystania z jednostki selektywne testowanie filtrowania, zobacz [uruchamianie selektywnych testów jednostkowych](../testing/selective-unit-tests.md).</span><span class="sxs-lookup"><span data-stu-id="4b895-177">For more information and examples on how to use selective unit test filtering, see [Running selective unit tests](../testing/selective-unit-tests.md).</span></span>

`-h|--help`

<span data-ttu-id="4b895-178">Drukuje krótki pomoc dotyczącą polecenia.</span><span class="sxs-lookup"><span data-stu-id="4b895-178">Prints out a short help for the command.</span></span>

`-l|--logger <LoggerUri/FriendlyName>`

<span data-ttu-id="4b895-179">Określa Rejestrator dla wyników badań.</span><span class="sxs-lookup"><span data-stu-id="4b895-179">Specifies a logger for test results.</span></span>

`--no-build`

<span data-ttu-id="4b895-180">Nie da się skompilować projektu testowego przed jego uruchomieniem.</span><span class="sxs-lookup"><span data-stu-id="4b895-180">Doesn't build the test project before running it.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="4b895-181">Katalog, w którym można znaleźć plików binarnych do uruchomienia.</span><span class="sxs-lookup"><span data-stu-id="4b895-181">Directory in which to find the binaries to run.</span></span>

`-s|--settings <SETTINGS_FILE>`

<span data-ttu-id="4b895-182">Ustawienia używane podczas uruchamiania testów.</span><span class="sxs-lookup"><span data-stu-id="4b895-182">Settings to use when running tests.</span></span>

`-t|--list-tests`

<span data-ttu-id="4b895-183">Listę wszystkich odnalezionych testów w bieżącym projekcie.</span><span class="sxs-lookup"><span data-stu-id="4b895-183">List all of the discovered tests in the current project.</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="4b895-184">Ustawia poziom szczegółowości polecenia.</span><span class="sxs-lookup"><span data-stu-id="4b895-184">Sets the verbosity level of the command.</span></span> <span data-ttu-id="4b895-185">Dozwolone wartości to `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, i `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="4b895-185">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

---

## <a name="examples"></a><span data-ttu-id="4b895-186">Przykłady</span><span class="sxs-lookup"><span data-stu-id="4b895-186">Examples</span></span>

<span data-ttu-id="4b895-187">Uruchom testy w projekcie w bieżącym katalogu:</span><span class="sxs-lookup"><span data-stu-id="4b895-187">Run the tests in the project in the current directory:</span></span>

`dotnet test`

<span data-ttu-id="4b895-188">Uruchom testy `test1` projektu:</span><span class="sxs-lookup"><span data-stu-id="4b895-188">Run the tests in the `test1` project:</span></span>

`dotnet test ~/projects/test1/test1.csproj`

<span data-ttu-id="4b895-189">Uruchom testy w projekcie w bieżącym katalogu i wygenerować plik wyników testu w formacie trx:</span><span class="sxs-lookup"><span data-stu-id="4b895-189">Run the tests in the project in the current directory and generate a test results file in the trx format:</span></span>

`dotnet test --logger:trx`

## <a name="filter-option-details"></a><span data-ttu-id="4b895-190">Szczegóły opcji filtru</span><span class="sxs-lookup"><span data-stu-id="4b895-190">Filter option details</span></span>

`--filter <EXPRESSION>`

<span data-ttu-id="4b895-191">`<Expression>` ma format `<property><operator><value>[|&<Expression>]`.</span><span class="sxs-lookup"><span data-stu-id="4b895-191">`<Expression>` has the format `<property><operator><value>[|&<Expression>]`.</span></span>

<span data-ttu-id="4b895-192">`<property>` jest to atrybut `Test Case`.</span><span class="sxs-lookup"><span data-stu-id="4b895-192">`<property>` is an attribute of the `Test Case`.</span></span> <span data-ttu-id="4b895-193">Poniżej przedstawiono właściwości obsługiwanych przez platform testów jednostkowych innych popularnych:</span><span class="sxs-lookup"><span data-stu-id="4b895-193">The following are the properties supported by popular unit test frameworks:</span></span>

| <span data-ttu-id="4b895-194">Struktury testowej</span><span class="sxs-lookup"><span data-stu-id="4b895-194">Test Framework</span></span> | <span data-ttu-id="4b895-195">Obsługiwanych właściwości</span><span class="sxs-lookup"><span data-stu-id="4b895-195">Supported properties</span></span>                                                                                      |
| -------------- | --------------------------------------------------------------------------------------------------------- |
| <span data-ttu-id="4b895-196">MSTest</span><span class="sxs-lookup"><span data-stu-id="4b895-196">MSTest</span></span>         | <ul><li><span data-ttu-id="4b895-197">FullyQualifiedName</span><span class="sxs-lookup"><span data-stu-id="4b895-197">FullyQualifiedName</span></span></li><li><span data-ttu-id="4b895-198">Nazwa</span><span class="sxs-lookup"><span data-stu-id="4b895-198">Name</span></span></li><li><span data-ttu-id="4b895-199">className</span><span class="sxs-lookup"><span data-stu-id="4b895-199">ClassName</span></span></li><li><span data-ttu-id="4b895-200">Priorytet</span><span class="sxs-lookup"><span data-stu-id="4b895-200">Priority</span></span></li><li><span data-ttu-id="4b895-201">TestCategory</span><span class="sxs-lookup"><span data-stu-id="4b895-201">TestCategory</span></span></li></ul> |
| <span data-ttu-id="4b895-202">xUnit</span><span class="sxs-lookup"><span data-stu-id="4b895-202">xUnit</span></span>          | <ul><li><span data-ttu-id="4b895-203">FullyQualifiedName</span><span class="sxs-lookup"><span data-stu-id="4b895-203">FullyQualifiedName</span></span></li><li><span data-ttu-id="4b895-204">Nazwa wyświetlana</span><span class="sxs-lookup"><span data-stu-id="4b895-204">DisplayName</span></span></li><li><span data-ttu-id="4b895-205">Cechy</span><span class="sxs-lookup"><span data-stu-id="4b895-205">Traits</span></span></li></ul>                                   |

<span data-ttu-id="4b895-206">`<operator>` Opisuje relację między właściwości i wartości:</span><span class="sxs-lookup"><span data-stu-id="4b895-206">The `<operator>` describes the relationship between the property and the value:</span></span>

| <span data-ttu-id="4b895-207">Operator</span><span class="sxs-lookup"><span data-stu-id="4b895-207">Operator</span></span> | <span data-ttu-id="4b895-208">Funkcja</span><span class="sxs-lookup"><span data-stu-id="4b895-208">Function</span></span>        |
| :------: | --------------- |
| `=`      | <span data-ttu-id="4b895-209">Dokładne dopasowanie</span><span class="sxs-lookup"><span data-stu-id="4b895-209">Exact match</span></span>     |
| `!=`     | <span data-ttu-id="4b895-210">Nie dokładne dopasowanie</span><span class="sxs-lookup"><span data-stu-id="4b895-210">Not exact match</span></span> |
| `~`      | <span data-ttu-id="4b895-211">Zawiera</span><span class="sxs-lookup"><span data-stu-id="4b895-211">Contains</span></span>        |

<span data-ttu-id="4b895-212">`<value>` jest to ciąg.</span><span class="sxs-lookup"><span data-stu-id="4b895-212">`<value>` is a string.</span></span> <span data-ttu-id="4b895-213">Wszystkie wyszukiwania jest rozróżniana wielkość liter.</span><span class="sxs-lookup"><span data-stu-id="4b895-213">All the lookups are case insensitive.</span></span>

<span data-ttu-id="4b895-214">Wyrażenie bez `<operator>` jest automatycznie traktowane jako `contains` na `FullyQualifiedName` właściwości (na przykład `dotnet test --filter xyz` jest taka sama jak `dotnet test --filter FullyQualifiedName~xyz`).</span><span class="sxs-lookup"><span data-stu-id="4b895-214">An expression without an `<operator>` is automatically considered as a `contains` on `FullyQualifiedName` property (for example, `dotnet test --filter xyz` is same as `dotnet test --filter FullyQualifiedName~xyz`).</span></span>

<span data-ttu-id="4b895-215">Wyrażenia może być łączone z operatorów warunkowych:</span><span class="sxs-lookup"><span data-stu-id="4b895-215">Expressions can be joined with conditional operators:</span></span>

| <span data-ttu-id="4b895-216">Operator</span><span class="sxs-lookup"><span data-stu-id="4b895-216">Operator</span></span>            | <span data-ttu-id="4b895-217">Funkcja</span><span class="sxs-lookup"><span data-stu-id="4b895-217">Function</span></span> |
| ------------------- | -------- |
| <code>&#124;</code> | <span data-ttu-id="4b895-218">LUB</span><span class="sxs-lookup"><span data-stu-id="4b895-218">OR</span></span>       |
| `&`                 | <span data-ttu-id="4b895-219">AND</span><span class="sxs-lookup"><span data-stu-id="4b895-219">AND</span></span>      |

<span data-ttu-id="4b895-220">Może być częścią wyrażenia w nawiasach przy użyciu operatorów warunkowych (na przykład `(Name~TestMethod1) | (Name~TestMethod2)`).</span><span class="sxs-lookup"><span data-stu-id="4b895-220">You can enclose expressions in parenthesis when using conditional operators (for example, `(Name~TestMethod1) | (Name~TestMethod2)`).</span></span>

<span data-ttu-id="4b895-221">Aby uzyskać dodatkowe informacje i przykłady dotyczące korzystania z jednostki selektywne testowanie filtrowania, zobacz [uruchamianie selektywnych testów jednostkowych](../testing/selective-unit-tests.md).</span><span class="sxs-lookup"><span data-stu-id="4b895-221">For more information and examples on how to use selective unit test filtering, see [Running selective unit tests](../testing/selective-unit-tests.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="4b895-222">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="4b895-222">See also</span></span>

* [<span data-ttu-id="4b895-223">Struktury i obiekty docelowe</span><span class="sxs-lookup"><span data-stu-id="4b895-223">Frameworks and Targets</span></span>](../../standard/frameworks.md)  
* [<span data-ttu-id="4b895-224">Katalog platformy .NET core środowiska uruchomieniowego identyfikator (RID)</span><span class="sxs-lookup"><span data-stu-id="4b895-224">.NET Core Runtime IDentifier (RID) catalog</span></span>](../rid-catalog.md)
