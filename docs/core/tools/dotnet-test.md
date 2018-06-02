---
title: polecenie test DotNet - .NET Core interfejsu wiersza polecenia
description: Polecenie test dotnet służy do wykonywania testów jednostkowych w danym projekcie.
author: mairaw
ms.author: mairaw
ms.date: 05/29/2018
ms.openlocfilehash: 8a10ac9175ee5fcf8649efbb07d8d382ac3afdc7
ms.sourcegitcommit: 3540f614fc94f77ca4ab58df66db2d0f4d52dfee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/01/2018
ms.locfileid: "34696273"
---
# <a name="dotnet-test"></a><span data-ttu-id="a4636-103">DotNet test</span><span class="sxs-lookup"><span data-stu-id="a4636-103">dotnet test</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="a4636-104">Nazwa</span><span class="sxs-lookup"><span data-stu-id="a4636-104">Name</span></span>

<span data-ttu-id="a4636-105">`dotnet test` — .NET testowanie sterowników używane do wykonywania testów jednostkowych.</span><span class="sxs-lookup"><span data-stu-id="a4636-105">`dotnet test` - .NET test driver used to execute unit tests.</span></span>

## <a name="synopsis"></a><span data-ttu-id="a4636-106">Streszczenie</span><span class="sxs-lookup"><span data-stu-id="a4636-106">Synopsis</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="a4636-107">Oprogramowanie .NET core 2.1</span><span class="sxs-lookup"><span data-stu-id="a4636-107">.NET Core 2.1</span></span>](#tab/netcore21)
```
dotnet test [<PROJECT>] [-a|--test-adapter-path] [--blame] [-c|--configuration] [--collect] [-d|--diag] [-f|--framework] [--filter]
    [-l|--logger] [--no-build] [--no-restore] [-o|--output] [-r|--results-directory] [-s|--settings] [-t|--list-tests] [-v|--verbosity]
dotnet test [-h|--help]
```
# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="a4636-108">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="a4636-108">.NET Core 2.0</span></span>](#tab/netcore20)
```
dotnet test [<PROJECT>] [-a|--test-adapter-path] [-c|--configuration] [--collect] [-d|--diag] [-f|--framework] [--filter]
    [-l|--logger] [--no-build] [--no-restore] [-o|--output] [-r|--results-directory] [-s|--settings] [-t|--list-tests] [-v|--verbosity]
dotnet test [-h|--help]
```
# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="a4636-109">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="a4636-109">.NET Core 1.x</span></span>](#tab/netcore1x)
```
dotnet test [<PROJECT>] [-a|--test-adapter-path] [-c|--configuration] [-d|--diag] [-f|--framework] [--filter] [-l|--logger] [--no-build] [-o|--output] [-s|--settings] [-t|--list-tests]  [-v|--verbosity]
dotnet test [-h|--help]
```
---

## <a name="description"></a><span data-ttu-id="a4636-110">Opis</span><span class="sxs-lookup"><span data-stu-id="a4636-110">Description</span></span>

<span data-ttu-id="a4636-111">`dotnet test` Polecenie służy do wykonywania testów jednostkowych w danym projekcie.</span><span class="sxs-lookup"><span data-stu-id="a4636-111">The `dotnet test` command is used to execute unit tests in a given project.</span></span> <span data-ttu-id="a4636-112">`dotnet test` Polecenie uruchamia aplikację konsoli test runner określony dla projektu.</span><span class="sxs-lookup"><span data-stu-id="a4636-112">The `dotnet test` command launches the test runner console application specified for a project.</span></span> <span data-ttu-id="a4636-113">Moduł uruchamiający wykonuje testy zdefiniowane dla struktury testów jednostkowych (na przykład MSTest, NUnit lub xUnit) i raporty powodzenie lub niepowodzenie każdego z testów.</span><span class="sxs-lookup"><span data-stu-id="a4636-113">The test runner executes the tests defined for a unit test framework (for example, MSTest, NUnit, or xUnit) and reports the success or failure of each test.</span></span> <span data-ttu-id="a4636-114">Moduł uruchamiający Biblioteka testów jednostkowych są dostarczane w pakietach NuGet i zostaną przywrócone jako zwykłej zależności projektu.</span><span class="sxs-lookup"><span data-stu-id="a4636-114">The test runner and the unit test library are packaged as NuGet packages and are restored as ordinary dependencies for the project.</span></span>

<span data-ttu-id="a4636-115">Projekty testowe Określ uruchamiający przy użyciu zwykłego `<PackageReference>` element, taki jak pokazano w poniższym przykładowym pliku projektu:</span><span class="sxs-lookup"><span data-stu-id="a4636-115">Test projects specify the test runner using an ordinary `<PackageReference>` element, as seen in the following sample project file:</span></span>

[!code-xml[XUnit Basic Template](../../../samples/snippets/csharp/xunit-test/xunit-test.csproj)]

## <a name="arguments"></a><span data-ttu-id="a4636-116">Argumenty</span><span class="sxs-lookup"><span data-stu-id="a4636-116">Arguments</span></span>

`PROJECT`

<span data-ttu-id="a4636-117">Ścieżka do projektu testowego.</span><span class="sxs-lookup"><span data-stu-id="a4636-117">Path to the test project.</span></span> <span data-ttu-id="a4636-118">Jeśli nie zostanie określony, domyślnie bieżącego katalogu.</span><span class="sxs-lookup"><span data-stu-id="a4636-118">If not specified, it defaults to current directory.</span></span>

## <a name="options"></a><span data-ttu-id="a4636-119">Opcje</span><span class="sxs-lookup"><span data-stu-id="a4636-119">Options</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="a4636-120">Oprogramowanie .NET core 2.1</span><span class="sxs-lookup"><span data-stu-id="a4636-120">.NET Core 2.1</span></span>](#tab/netcore21)

`-a|--test-adapter-path <PATH_TO_ADAPTER>`

<span data-ttu-id="a4636-121">Używa niestandardowych adapterów testowych z określonej ścieżki w uruchomieniu testu.</span><span class="sxs-lookup"><span data-stu-id="a4636-121">Use the custom test adapters from the specified path in the test run.</span></span>

`--blame`

<span data-ttu-id="a4636-122">Uruchamia testy w trybie winy.</span><span class="sxs-lookup"><span data-stu-id="a4636-122">Runs the tests in blame mode.</span></span> <span data-ttu-id="a4636-123">Ta opcja jest pomocna w izolowanie testów problemy powodujące hosta testów do awarii.</span><span class="sxs-lookup"><span data-stu-id="a4636-123">This option is helpful in isolating the problematic tests causing test host to crash.</span></span> <span data-ttu-id="a4636-124">Tworzy plik wyjściowy w bieżącym katalogu jako *Sequence.xml* który przechwytuje kolejność wykonywania testów przed tej awarii.</span><span class="sxs-lookup"><span data-stu-id="a4636-124">It creates an output file in the current directory as *Sequence.xml* that captures the order of tests execution before the crash.</span></span>

`-c|--configuration {Debug|Release}`

<span data-ttu-id="a4636-125">Definiuje konfigurację kompilacji.</span><span class="sxs-lookup"><span data-stu-id="a4636-125">Defines the build configuration.</span></span> <span data-ttu-id="a4636-126">Wartość domyślna to `Debug`, ale konfiguracja projektu można zastąpić to ustawienie domyślne zestawu SDK.</span><span class="sxs-lookup"><span data-stu-id="a4636-126">The default value is `Debug`, but your project's configuration could override this default SDK setting.</span></span>

`--collect <DATA_COLLECTOR_FRIENDLY_NAME>`

<span data-ttu-id="a4636-127">Włącza moduł zbierający dane dla uruchomienia testu.</span><span class="sxs-lookup"><span data-stu-id="a4636-127">Enables data collector for the test run.</span></span> <span data-ttu-id="a4636-128">Aby uzyskać więcej informacji, zobacz [monitora i analizować uruchomienia testu](https://aka.ms/vstest-collect).</span><span class="sxs-lookup"><span data-stu-id="a4636-128">For more information, see [Monitor and analyze test run](https://aka.ms/vstest-collect).</span></span>

`-d|--diag <PATH_TO_DIAGNOSTICS_FILE>`

<span data-ttu-id="a4636-129">Włącza tryb diagnostycznych dla testu platformy i zapisu komunikaty diagnostyczne do określonego pliku.</span><span class="sxs-lookup"><span data-stu-id="a4636-129">Enables diagnostic mode for the test platform and write diagnostic messages to the specified file.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="a4636-130">Wyszukuje pliki binarne testów dla określonego [framework](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="a4636-130">Looks for test binaries for a specific [framework](../../standard/frameworks.md).</span></span>

`--filter <EXPRESSION>`

<span data-ttu-id="a4636-131">Odfiltrowuje testy w bieżącym projekcie przy użyciu danego wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="a4636-131">Filters out tests in the current project using the given expression.</span></span> <span data-ttu-id="a4636-132">Aby uzyskać więcej informacji, zobacz [opcję Szczegóły filtru](#filter-option-details) sekcji.</span><span class="sxs-lookup"><span data-stu-id="a4636-132">For more information, see the [Filter option details](#filter-option-details) section.</span></span> <span data-ttu-id="a4636-133">Aby uzyskać dodatkowe informacje i przykłady dotyczące sposobu używania filtrowanie testów jednostki selektywnego, zobacz [przeprowadzanie testów jednostkowych selektywne](../testing/selective-unit-tests.md).</span><span class="sxs-lookup"><span data-stu-id="a4636-133">For more information and examples on how to use selective unit test filtering, see [Running selective unit tests](../testing/selective-unit-tests.md).</span></span>

`-h|--help`

<span data-ttu-id="a4636-134">Drukuje krótkich pomocy dla polecenia.</span><span class="sxs-lookup"><span data-stu-id="a4636-134">Prints out a short help for the command.</span></span>

`-l|--logger <LoggerUri/FriendlyName>`

<span data-ttu-id="a4636-135">Określa Rejestrator dla wyników testu.</span><span class="sxs-lookup"><span data-stu-id="a4636-135">Specifies a logger for test results.</span></span>

`--no-build`

<span data-ttu-id="a4636-136">Nie można utworzyć projektu testowego przed jego uruchomieniem.</span><span class="sxs-lookup"><span data-stu-id="a4636-136">Doesn't build the test project before running it.</span></span> <span data-ttu-id="a4636-137">Niejawne także ustawia `--no-restore` flagi.</span><span class="sxs-lookup"><span data-stu-id="a4636-137">It also implicit sets the `--no-restore` flag.</span></span>

`--no-restore`

<span data-ttu-id="a4636-138">Podczas uruchamiania polecenia przywracania niejawne nie jest wykonywana.</span><span class="sxs-lookup"><span data-stu-id="a4636-138">Doesn't execute an implicit restore when running the command.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="a4636-139">Katalog, w którym można znaleźć plików binarnych do uruchomienia.</span><span class="sxs-lookup"><span data-stu-id="a4636-139">Directory in which to find the binaries to run.</span></span>

`-r|--results-directory <PATH>`

<span data-ttu-id="a4636-140">Katalog, w której będzie można umieścić wyników testu.</span><span class="sxs-lookup"><span data-stu-id="a4636-140">The directory where the test results are going to be placed.</span></span> <span data-ttu-id="a4636-141">Jeśli określony katalog nie istnieje, jest tworzony.</span><span class="sxs-lookup"><span data-stu-id="a4636-141">If the specified directory doesn't exist, it's created.</span></span>

`-s|--settings <SETTINGS_FILE>`

<span data-ttu-id="a4636-142">Ustawienia używane podczas uruchamiania testów.</span><span class="sxs-lookup"><span data-stu-id="a4636-142">Settings to use when running tests.</span></span>

`-t|--list-tests`

<span data-ttu-id="a4636-143">Lista wszystkich odnalezionych testów w bieżącym projekcie.</span><span class="sxs-lookup"><span data-stu-id="a4636-143">List all of the discovered tests in the current project.</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="a4636-144">Ustawia poziom szczegółowości polecenia.</span><span class="sxs-lookup"><span data-stu-id="a4636-144">Sets the verbosity level of the command.</span></span> <span data-ttu-id="a4636-145">Dozwolone wartości to `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, i `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="a4636-145">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="a4636-146">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="a4636-146">.NET Core 2.0</span></span>](#tab/netcore20)

`-a|--test-adapter-path <PATH_TO_ADAPTER>`

<span data-ttu-id="a4636-147">Używa niestandardowych adapterów testowych z określonej ścieżki w uruchomieniu testu.</span><span class="sxs-lookup"><span data-stu-id="a4636-147">Use the custom test adapters from the specified path in the test run.</span></span>

`-c|--configuration {Debug|Release}`

<span data-ttu-id="a4636-148">Definiuje konfigurację kompilacji.</span><span class="sxs-lookup"><span data-stu-id="a4636-148">Defines the build configuration.</span></span> <span data-ttu-id="a4636-149">Wartość domyślna to `Debug`, ale konfiguracja projektu można zastąpić to ustawienie domyślne zestawu SDK.</span><span class="sxs-lookup"><span data-stu-id="a4636-149">The default value is `Debug`, but your project's configuration could override this default SDK setting.</span></span>

`--collect <DATA_COLLECTOR_FRIENDLY_NAME>`

<span data-ttu-id="a4636-150">Włącza moduł zbierający dane dla uruchomienia testu.</span><span class="sxs-lookup"><span data-stu-id="a4636-150">Enables data collector for the test run.</span></span> <span data-ttu-id="a4636-151">Aby uzyskać więcej informacji, zobacz [monitora i analizować uruchomienia testu](https://aka.ms/vstest-collect).</span><span class="sxs-lookup"><span data-stu-id="a4636-151">For more information, see [Monitor and analyze test run](https://aka.ms/vstest-collect).</span></span>

`-d|--diag <PATH_TO_DIAGNOSTICS_FILE>`

<span data-ttu-id="a4636-152">Włącza tryb diagnostycznych dla testu platformy i zapisu komunikaty diagnostyczne do określonego pliku.</span><span class="sxs-lookup"><span data-stu-id="a4636-152">Enables diagnostic mode for the test platform and write diagnostic messages to the specified file.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="a4636-153">Wyszukuje pliki binarne testów dla określonego [framework](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="a4636-153">Looks for test binaries for a specific [framework](../../standard/frameworks.md).</span></span>

`--filter <EXPRESSION>`

<span data-ttu-id="a4636-154">Odfiltrowuje testy w bieżącym projekcie przy użyciu danego wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="a4636-154">Filters out tests in the current project using the given expression.</span></span> <span data-ttu-id="a4636-155">Aby uzyskać więcej informacji, zobacz [opcję Szczegóły filtru](#filter-option-details) sekcji.</span><span class="sxs-lookup"><span data-stu-id="a4636-155">For more information, see the [Filter option details](#filter-option-details) section.</span></span> <span data-ttu-id="a4636-156">Aby uzyskać dodatkowe informacje i przykłady dotyczące sposobu używania filtrowanie testów jednostki selektywnego, zobacz [przeprowadzanie testów jednostkowych selektywne](../testing/selective-unit-tests.md).</span><span class="sxs-lookup"><span data-stu-id="a4636-156">For more information and examples on how to use selective unit test filtering, see [Running selective unit tests](../testing/selective-unit-tests.md).</span></span>

`-h|--help`

<span data-ttu-id="a4636-157">Drukuje krótkich pomocy dla polecenia.</span><span class="sxs-lookup"><span data-stu-id="a4636-157">Prints out a short help for the command.</span></span>

`-l|--logger <LoggerUri/FriendlyName>`

<span data-ttu-id="a4636-158">Określa Rejestrator dla wyników testu.</span><span class="sxs-lookup"><span data-stu-id="a4636-158">Specifies a logger for test results.</span></span>

`--no-build`

<span data-ttu-id="a4636-159">Nie można utworzyć projektu testowego przed jego uruchomieniem.</span><span class="sxs-lookup"><span data-stu-id="a4636-159">Doesn't build the test project before running it.</span></span> <span data-ttu-id="a4636-160">Niejawne także ustawia `--no-restore` flagi.</span><span class="sxs-lookup"><span data-stu-id="a4636-160">It also implicit sets the `--no-restore` flag.</span></span>

`--no-restore`

<span data-ttu-id="a4636-161">Podczas uruchamiania polecenia przywracania niejawne nie jest wykonywana.</span><span class="sxs-lookup"><span data-stu-id="a4636-161">Doesn't execute an implicit restore when running the command.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="a4636-162">Katalog, w którym można znaleźć plików binarnych do uruchomienia.</span><span class="sxs-lookup"><span data-stu-id="a4636-162">Directory in which to find the binaries to run.</span></span>

`-r|--results-directory <PATH>`

<span data-ttu-id="a4636-163">Katalog, w której będzie można umieścić wyników testu.</span><span class="sxs-lookup"><span data-stu-id="a4636-163">The directory where the test results are going to be placed.</span></span> <span data-ttu-id="a4636-164">Jeśli określony katalog nie istnieje, jest tworzony.</span><span class="sxs-lookup"><span data-stu-id="a4636-164">If the specified directory doesn't exist, it's created.</span></span>

`-s|--settings <SETTINGS_FILE>`

<span data-ttu-id="a4636-165">Ustawienia używane podczas uruchamiania testów.</span><span class="sxs-lookup"><span data-stu-id="a4636-165">Settings to use when running tests.</span></span>

`-t|--list-tests`

<span data-ttu-id="a4636-166">Lista wszystkich odnalezionych testów w bieżącym projekcie.</span><span class="sxs-lookup"><span data-stu-id="a4636-166">List all of the discovered tests in the current project.</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="a4636-167">Ustawia poziom szczegółowości polecenia.</span><span class="sxs-lookup"><span data-stu-id="a4636-167">Sets the verbosity level of the command.</span></span> <span data-ttu-id="a4636-168">Dozwolone wartości to `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, i `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="a4636-168">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="a4636-169">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="a4636-169">.NET Core 1.x</span></span>](#tab/netcore1x)

`-a|--test-adapter-path <PATH_TO_ADAPTER>`

<span data-ttu-id="a4636-170">Używa niestandardowych adapterów testowych z określonej ścieżki w uruchomieniu testu.</span><span class="sxs-lookup"><span data-stu-id="a4636-170">Use the custom test adapters from the specified path in the test run.</span></span>

`-c|--configuration {Debug|Release}`

<span data-ttu-id="a4636-171">Definiuje konfigurację kompilacji.</span><span class="sxs-lookup"><span data-stu-id="a4636-171">Defines the build configuration.</span></span> <span data-ttu-id="a4636-172">Wartość domyślna to `Debug`, ale konfiguracja projektu można zastąpić to ustawienie domyślne zestawu SDK.</span><span class="sxs-lookup"><span data-stu-id="a4636-172">The default value is `Debug`, but your project's configuration could override this default SDK setting.</span></span>

`-d|--diag <PATH_TO_DIAGNOSTICS_FILE>`

<span data-ttu-id="a4636-173">Włącza tryb diagnostycznych dla testu platformy i zapisu komunikaty diagnostyczne do określonego pliku.</span><span class="sxs-lookup"><span data-stu-id="a4636-173">Enables diagnostic mode for the test platform and write diagnostic messages to the specified file.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="a4636-174">Wyszukuje pliki binarne testów dla określonego [framework](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="a4636-174">Looks for test binaries for a specific [framework](../../standard/frameworks.md).</span></span>

`--filter <EXPRESSION>`

<span data-ttu-id="a4636-175">Odfiltrowuje testy w bieżącym projekcie przy użyciu danego wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="a4636-175">Filters out tests in the current project using the given expression.</span></span> <span data-ttu-id="a4636-176">Aby uzyskać więcej informacji, zobacz [opcję Szczegóły filtru](#filter-option-details) sekcji.</span><span class="sxs-lookup"><span data-stu-id="a4636-176">For more information, see the [Filter option details](#filter-option-details) section.</span></span> <span data-ttu-id="a4636-177">Aby uzyskać dodatkowe informacje i przykłady dotyczące sposobu używania filtrowanie testów jednostki selektywnego, zobacz [przeprowadzanie testów jednostkowych selektywne](../testing/selective-unit-tests.md).</span><span class="sxs-lookup"><span data-stu-id="a4636-177">For more information and examples on how to use selective unit test filtering, see [Running selective unit tests](../testing/selective-unit-tests.md).</span></span>

`-h|--help`

<span data-ttu-id="a4636-178">Drukuje krótkich pomocy dla polecenia.</span><span class="sxs-lookup"><span data-stu-id="a4636-178">Prints out a short help for the command.</span></span>

`-l|--logger <LoggerUri/FriendlyName>`

<span data-ttu-id="a4636-179">Określa Rejestrator dla wyników testu.</span><span class="sxs-lookup"><span data-stu-id="a4636-179">Specifies a logger for test results.</span></span>

`--no-build`

<span data-ttu-id="a4636-180">Nie można utworzyć projektu testowego przed jego uruchomieniem.</span><span class="sxs-lookup"><span data-stu-id="a4636-180">Doesn't build the test project before running it.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="a4636-181">Katalog, w którym można znaleźć plików binarnych do uruchomienia.</span><span class="sxs-lookup"><span data-stu-id="a4636-181">Directory in which to find the binaries to run.</span></span>

`-s|--settings <SETTINGS_FILE>`

<span data-ttu-id="a4636-182">Ustawienia używane podczas uruchamiania testów.</span><span class="sxs-lookup"><span data-stu-id="a4636-182">Settings to use when running tests.</span></span>

`-t|--list-tests`

<span data-ttu-id="a4636-183">Lista wszystkich odnalezionych testów w bieżącym projekcie.</span><span class="sxs-lookup"><span data-stu-id="a4636-183">List all of the discovered tests in the current project.</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="a4636-184">Ustawia poziom szczegółowości polecenia.</span><span class="sxs-lookup"><span data-stu-id="a4636-184">Sets the verbosity level of the command.</span></span> <span data-ttu-id="a4636-185">Dozwolone wartości to `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, i `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="a4636-185">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

---

## <a name="examples"></a><span data-ttu-id="a4636-186">Przykłady</span><span class="sxs-lookup"><span data-stu-id="a4636-186">Examples</span></span>

<span data-ttu-id="a4636-187">Uruchom testy w projekcie w bieżącym katalogu:</span><span class="sxs-lookup"><span data-stu-id="a4636-187">Run the tests in the project in the current directory:</span></span>

`dotnet test`

<span data-ttu-id="a4636-188">Uruchom testy `test1` projektu:</span><span class="sxs-lookup"><span data-stu-id="a4636-188">Run the tests in the `test1` project:</span></span>

`dotnet test ~/projects/test1/test1.csproj`

## <a name="filter-option-details"></a><span data-ttu-id="a4636-189">Szczegóły opcji filtru</span><span class="sxs-lookup"><span data-stu-id="a4636-189">Filter option details</span></span>

`--filter <EXPRESSION>`

<span data-ttu-id="a4636-190">`<Expression>` ma format `<property><operator><value>[|&<Expression>]`.</span><span class="sxs-lookup"><span data-stu-id="a4636-190">`<Expression>` has the format `<property><operator><value>[|&<Expression>]`.</span></span>

<span data-ttu-id="a4636-191">`<property>` atrybut `Test Case`.</span><span class="sxs-lookup"><span data-stu-id="a4636-191">`<property>` is an attribute of the `Test Case`.</span></span> <span data-ttu-id="a4636-192">Właściwości obsługiwanych przez platform testów jednostkowych popularnych są następujące:</span><span class="sxs-lookup"><span data-stu-id="a4636-192">The following are the properties supported by popular unit test frameworks:</span></span>

| <span data-ttu-id="a4636-193">Struktury testowej</span><span class="sxs-lookup"><span data-stu-id="a4636-193">Test Framework</span></span> | <span data-ttu-id="a4636-194">Obsługiwanych właściwości</span><span class="sxs-lookup"><span data-stu-id="a4636-194">Supported properties</span></span>                                                                                      |
| -------------- | --------------------------------------------------------------------------------------------------------- |
| <span data-ttu-id="a4636-195">MSTest</span><span class="sxs-lookup"><span data-stu-id="a4636-195">MSTest</span></span>         | <ul><li><span data-ttu-id="a4636-196">FullyQualifiedName</span><span class="sxs-lookup"><span data-stu-id="a4636-196">FullyQualifiedName</span></span></li><li><span data-ttu-id="a4636-197">Nazwa</span><span class="sxs-lookup"><span data-stu-id="a4636-197">Name</span></span></li><li><span data-ttu-id="a4636-198">className</span><span class="sxs-lookup"><span data-stu-id="a4636-198">ClassName</span></span></li><li><span data-ttu-id="a4636-199">Priorytet</span><span class="sxs-lookup"><span data-stu-id="a4636-199">Priority</span></span></li><li><span data-ttu-id="a4636-200">TestCategory</span><span class="sxs-lookup"><span data-stu-id="a4636-200">TestCategory</span></span></li></ul> |
| <span data-ttu-id="a4636-201">xUnit</span><span class="sxs-lookup"><span data-stu-id="a4636-201">xUnit</span></span>          | <ul><li><span data-ttu-id="a4636-202">FullyQualifiedName</span><span class="sxs-lookup"><span data-stu-id="a4636-202">FullyQualifiedName</span></span></li><li><span data-ttu-id="a4636-203">Nazwa wyświetlana</span><span class="sxs-lookup"><span data-stu-id="a4636-203">DisplayName</span></span></li><li><span data-ttu-id="a4636-204">Cechy</span><span class="sxs-lookup"><span data-stu-id="a4636-204">Traits</span></span></li></ul>                                   |

<span data-ttu-id="a4636-205">`<operator>` Opisuje relację między właściwości i wartość:</span><span class="sxs-lookup"><span data-stu-id="a4636-205">The `<operator>` describes the relationship between the property and the value:</span></span>

| <span data-ttu-id="a4636-206">Operator</span><span class="sxs-lookup"><span data-stu-id="a4636-206">Operator</span></span> | <span data-ttu-id="a4636-207">Funkcja</span><span class="sxs-lookup"><span data-stu-id="a4636-207">Function</span></span>        |
| :------: | --------------- |
| `=`      | <span data-ttu-id="a4636-208">Dokładnego dopasowania</span><span class="sxs-lookup"><span data-stu-id="a4636-208">Exact match</span></span>     |
| `!=`     | <span data-ttu-id="a4636-209">Nie dokładnego dopasowania</span><span class="sxs-lookup"><span data-stu-id="a4636-209">Not exact match</span></span> |
| `~`      | <span data-ttu-id="a4636-210">Zawiera</span><span class="sxs-lookup"><span data-stu-id="a4636-210">Contains</span></span>        |

<span data-ttu-id="a4636-211">`<value>` jest to ciąg.</span><span class="sxs-lookup"><span data-stu-id="a4636-211">`<value>` is a string.</span></span> <span data-ttu-id="a4636-212">Wszystkie wyszukiwania są bez uwzględniania wielkości liter.</span><span class="sxs-lookup"><span data-stu-id="a4636-212">All the lookups are case insensitive.</span></span>

<span data-ttu-id="a4636-213">Wyrażenia bez `<operator>` jest automatycznie traktowane jako `contains` na `FullyQualifiedName` właściwości (na przykład `dotnet test --filter xyz` jest taka sama jak `dotnet test --filter FullyQualifiedName~xyz`).</span><span class="sxs-lookup"><span data-stu-id="a4636-213">An expression without an `<operator>` is automatically considered as a `contains` on `FullyQualifiedName` property (for example, `dotnet test --filter xyz` is same as `dotnet test --filter FullyQualifiedName~xyz`).</span></span>

<span data-ttu-id="a4636-214">Może być częścią wyrażenia z operatorami warunkowego:</span><span class="sxs-lookup"><span data-stu-id="a4636-214">Expressions can be joined with conditional operators:</span></span>

| <span data-ttu-id="a4636-215">Operator</span><span class="sxs-lookup"><span data-stu-id="a4636-215">Operator</span></span>            | <span data-ttu-id="a4636-216">Funkcja</span><span class="sxs-lookup"><span data-stu-id="a4636-216">Function</span></span> |
| ------------------- | -------- |
| <code>&#124;</code> | <span data-ttu-id="a4636-217">LUB</span><span class="sxs-lookup"><span data-stu-id="a4636-217">OR</span></span>       |
| `&`                 | <span data-ttu-id="a4636-218">AND</span><span class="sxs-lookup"><span data-stu-id="a4636-218">AND</span></span>      |

<span data-ttu-id="a4636-219">Może być częścią wyrażenia w nawiasach przy użyciu operatorów warunkowych (na przykład `(Name~TestMethod1) | (Name~TestMethod2)`).</span><span class="sxs-lookup"><span data-stu-id="a4636-219">You can enclose expressions in parenthesis when using conditional operators (for example, `(Name~TestMethod1) | (Name~TestMethod2)`).</span></span>

<span data-ttu-id="a4636-220">Aby uzyskać dodatkowe informacje i przykłady dotyczące sposobu używania filtrowanie testów jednostki selektywnego, zobacz [przeprowadzanie testów jednostkowych selektywne](../testing/selective-unit-tests.md).</span><span class="sxs-lookup"><span data-stu-id="a4636-220">For more information and examples on how to use selective unit test filtering, see [Running selective unit tests](../testing/selective-unit-tests.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="a4636-221">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a4636-221">See also</span></span>

[<span data-ttu-id="a4636-222">Struktury i cele</span><span class="sxs-lookup"><span data-stu-id="a4636-222">Frameworks and Targets</span></span>](../../standard/frameworks.md)  
[<span data-ttu-id="a4636-223">Katalogu .NET core środowiska uruchomieniowego identyfikator (RID)</span><span class="sxs-lookup"><span data-stu-id="a4636-223">.NET Core Runtime IDentifier (RID) catalog</span></span>](../rid-catalog.md)
