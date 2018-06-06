---
title: polecenie test DotNet - .NET Core interfejsu wiersza polecenia
description: Polecenie test dotnet służy do wykonywania testów jednostkowych w danym projekcie.
author: mairaw
ms.author: mairaw
ms.date: 05/29/2018
ms.openlocfilehash: 8a10ac9175ee5fcf8649efbb07d8d382ac3afdc7
ms.sourcegitcommit: bbf70abe6b46073148f78cbf0619de6092b5800c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2018
ms.locfileid: "34696273"
---
# <a name="dotnet-test"></a><span data-ttu-id="832c8-103">DotNet test</span><span class="sxs-lookup"><span data-stu-id="832c8-103">dotnet test</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="832c8-104">Nazwa</span><span class="sxs-lookup"><span data-stu-id="832c8-104">Name</span></span>

<span data-ttu-id="832c8-105">`dotnet test` — .NET testowanie sterowników używane do wykonywania testów jednostkowych.</span><span class="sxs-lookup"><span data-stu-id="832c8-105">`dotnet test` - .NET test driver used to execute unit tests.</span></span>

## <a name="synopsis"></a><span data-ttu-id="832c8-106">Streszczenie</span><span class="sxs-lookup"><span data-stu-id="832c8-106">Synopsis</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="832c8-107">Oprogramowanie .NET core 2.1</span><span class="sxs-lookup"><span data-stu-id="832c8-107">.NET Core 2.1</span></span>](#tab/netcore21)
```
dotnet test [<PROJECT>] [-a|--test-adapter-path] [--blame] [-c|--configuration] [--collect] [-d|--diag] [-f|--framework] [--filter]
    [-l|--logger] [--no-build] [--no-restore] [-o|--output] [-r|--results-directory] [-s|--settings] [-t|--list-tests] [-v|--verbosity]
dotnet test [-h|--help]
```
# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="832c8-108">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="832c8-108">.NET Core 2.0</span></span>](#tab/netcore20)
```
dotnet test [<PROJECT>] [-a|--test-adapter-path] [-c|--configuration] [--collect] [-d|--diag] [-f|--framework] [--filter]
    [-l|--logger] [--no-build] [--no-restore] [-o|--output] [-r|--results-directory] [-s|--settings] [-t|--list-tests] [-v|--verbosity]
dotnet test [-h|--help]
```
# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="832c8-109">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="832c8-109">.NET Core 1.x</span></span>](#tab/netcore1x)
```
dotnet test [<PROJECT>] [-a|--test-adapter-path] [-c|--configuration] [-d|--diag] [-f|--framework] [--filter] [-l|--logger] [--no-build] [-o|--output] [-s|--settings] [-t|--list-tests]  [-v|--verbosity]
dotnet test [-h|--help]
```
---

## <a name="description"></a><span data-ttu-id="832c8-110">Opis</span><span class="sxs-lookup"><span data-stu-id="832c8-110">Description</span></span>

<span data-ttu-id="832c8-111">`dotnet test` Polecenie służy do wykonywania testów jednostkowych w danym projekcie.</span><span class="sxs-lookup"><span data-stu-id="832c8-111">The `dotnet test` command is used to execute unit tests in a given project.</span></span> <span data-ttu-id="832c8-112">`dotnet test` Polecenie uruchamia aplikację konsoli test runner określony dla projektu.</span><span class="sxs-lookup"><span data-stu-id="832c8-112">The `dotnet test` command launches the test runner console application specified for a project.</span></span> <span data-ttu-id="832c8-113">Moduł uruchamiający wykonuje testy zdefiniowane dla struktury testów jednostkowych (na przykład MSTest, NUnit lub xUnit) i raporty powodzenie lub niepowodzenie każdego z testów.</span><span class="sxs-lookup"><span data-stu-id="832c8-113">The test runner executes the tests defined for a unit test framework (for example, MSTest, NUnit, or xUnit) and reports the success or failure of each test.</span></span> <span data-ttu-id="832c8-114">Moduł uruchamiający Biblioteka testów jednostkowych są dostarczane w pakietach NuGet i zostaną przywrócone jako zwykłej zależności projektu.</span><span class="sxs-lookup"><span data-stu-id="832c8-114">The test runner and the unit test library are packaged as NuGet packages and are restored as ordinary dependencies for the project.</span></span>

<span data-ttu-id="832c8-115">Projekty testowe Określ uruchamiający przy użyciu zwykłego `<PackageReference>` element, taki jak pokazano w poniższym przykładowym pliku projektu:</span><span class="sxs-lookup"><span data-stu-id="832c8-115">Test projects specify the test runner using an ordinary `<PackageReference>` element, as seen in the following sample project file:</span></span>

[!code-xml[XUnit Basic Template](../../../samples/snippets/csharp/xunit-test/xunit-test.csproj)]

## <a name="arguments"></a><span data-ttu-id="832c8-116">Argumenty</span><span class="sxs-lookup"><span data-stu-id="832c8-116">Arguments</span></span>

`PROJECT`

<span data-ttu-id="832c8-117">Ścieżka do projektu testowego.</span><span class="sxs-lookup"><span data-stu-id="832c8-117">Path to the test project.</span></span> <span data-ttu-id="832c8-118">Jeśli nie zostanie określony, domyślnie bieżącego katalogu.</span><span class="sxs-lookup"><span data-stu-id="832c8-118">If not specified, it defaults to current directory.</span></span>

## <a name="options"></a><span data-ttu-id="832c8-119">Opcje</span><span class="sxs-lookup"><span data-stu-id="832c8-119">Options</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="832c8-120">Oprogramowanie .NET core 2.1</span><span class="sxs-lookup"><span data-stu-id="832c8-120">.NET Core 2.1</span></span>](#tab/netcore21)

`-a|--test-adapter-path <PATH_TO_ADAPTER>`

<span data-ttu-id="832c8-121">Używa niestandardowych adapterów testowych z określonej ścieżki w uruchomieniu testu.</span><span class="sxs-lookup"><span data-stu-id="832c8-121">Use the custom test adapters from the specified path in the test run.</span></span>

`--blame`

<span data-ttu-id="832c8-122">Uruchamia testy w trybie winy.</span><span class="sxs-lookup"><span data-stu-id="832c8-122">Runs the tests in blame mode.</span></span> <span data-ttu-id="832c8-123">Ta opcja jest pomocna w izolowanie testów problemy powodujące hosta testów do awarii.</span><span class="sxs-lookup"><span data-stu-id="832c8-123">This option is helpful in isolating the problematic tests causing test host to crash.</span></span> <span data-ttu-id="832c8-124">Tworzy plik wyjściowy w bieżącym katalogu jako *Sequence.xml* który przechwytuje kolejność wykonywania testów przed tej awarii.</span><span class="sxs-lookup"><span data-stu-id="832c8-124">It creates an output file in the current directory as *Sequence.xml* that captures the order of tests execution before the crash.</span></span>

`-c|--configuration {Debug|Release}`

<span data-ttu-id="832c8-125">Definiuje konfigurację kompilacji.</span><span class="sxs-lookup"><span data-stu-id="832c8-125">Defines the build configuration.</span></span> <span data-ttu-id="832c8-126">Wartość domyślna to `Debug`, ale konfiguracja projektu można zastąpić to ustawienie domyślne zestawu SDK.</span><span class="sxs-lookup"><span data-stu-id="832c8-126">The default value is `Debug`, but your project's configuration could override this default SDK setting.</span></span>

`--collect <DATA_COLLECTOR_FRIENDLY_NAME>`

<span data-ttu-id="832c8-127">Włącza moduł zbierający dane dla uruchomienia testu.</span><span class="sxs-lookup"><span data-stu-id="832c8-127">Enables data collector for the test run.</span></span> <span data-ttu-id="832c8-128">Aby uzyskać więcej informacji, zobacz [monitora i analizować uruchomienia testu](https://aka.ms/vstest-collect).</span><span class="sxs-lookup"><span data-stu-id="832c8-128">For more information, see [Monitor and analyze test run](https://aka.ms/vstest-collect).</span></span>

`-d|--diag <PATH_TO_DIAGNOSTICS_FILE>`

<span data-ttu-id="832c8-129">Włącza tryb diagnostycznych dla testu platformy i zapisu komunikaty diagnostyczne do określonego pliku.</span><span class="sxs-lookup"><span data-stu-id="832c8-129">Enables diagnostic mode for the test platform and write diagnostic messages to the specified file.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="832c8-130">Wyszukuje pliki binarne testów dla określonego [framework](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="832c8-130">Looks for test binaries for a specific [framework](../../standard/frameworks.md).</span></span>

`--filter <EXPRESSION>`

<span data-ttu-id="832c8-131">Odfiltrowuje testy w bieżącym projekcie przy użyciu danego wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="832c8-131">Filters out tests in the current project using the given expression.</span></span> <span data-ttu-id="832c8-132">Aby uzyskać więcej informacji, zobacz [opcję Szczegóły filtru](#filter-option-details) sekcji.</span><span class="sxs-lookup"><span data-stu-id="832c8-132">For more information, see the [Filter option details](#filter-option-details) section.</span></span> <span data-ttu-id="832c8-133">Aby uzyskać dodatkowe informacje i przykłady dotyczące sposobu używania filtrowanie testów jednostki selektywnego, zobacz [przeprowadzanie testów jednostkowych selektywne](../testing/selective-unit-tests.md).</span><span class="sxs-lookup"><span data-stu-id="832c8-133">For more information and examples on how to use selective unit test filtering, see [Running selective unit tests](../testing/selective-unit-tests.md).</span></span>

`-h|--help`

<span data-ttu-id="832c8-134">Drukuje krótkich pomocy dla polecenia.</span><span class="sxs-lookup"><span data-stu-id="832c8-134">Prints out a short help for the command.</span></span>

`-l|--logger <LoggerUri/FriendlyName>`

<span data-ttu-id="832c8-135">Określa Rejestrator dla wyników testu.</span><span class="sxs-lookup"><span data-stu-id="832c8-135">Specifies a logger for test results.</span></span>

`--no-build`

<span data-ttu-id="832c8-136">Nie można utworzyć projektu testowego przed jego uruchomieniem.</span><span class="sxs-lookup"><span data-stu-id="832c8-136">Doesn't build the test project before running it.</span></span> <span data-ttu-id="832c8-137">Niejawne także ustawia `--no-restore` flagi.</span><span class="sxs-lookup"><span data-stu-id="832c8-137">It also implicit sets the `--no-restore` flag.</span></span>

`--no-restore`

<span data-ttu-id="832c8-138">Podczas uruchamiania polecenia przywracania niejawne nie jest wykonywana.</span><span class="sxs-lookup"><span data-stu-id="832c8-138">Doesn't execute an implicit restore when running the command.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="832c8-139">Katalog, w którym można znaleźć plików binarnych do uruchomienia.</span><span class="sxs-lookup"><span data-stu-id="832c8-139">Directory in which to find the binaries to run.</span></span>

`-r|--results-directory <PATH>`

<span data-ttu-id="832c8-140">Katalog, w której będzie można umieścić wyników testu.</span><span class="sxs-lookup"><span data-stu-id="832c8-140">The directory where the test results are going to be placed.</span></span> <span data-ttu-id="832c8-141">Jeśli określony katalog nie istnieje, jest tworzony.</span><span class="sxs-lookup"><span data-stu-id="832c8-141">If the specified directory doesn't exist, it's created.</span></span>

`-s|--settings <SETTINGS_FILE>`

<span data-ttu-id="832c8-142">Ustawienia używane podczas uruchamiania testów.</span><span class="sxs-lookup"><span data-stu-id="832c8-142">Settings to use when running tests.</span></span>

`-t|--list-tests`

<span data-ttu-id="832c8-143">Lista wszystkich odnalezionych testów w bieżącym projekcie.</span><span class="sxs-lookup"><span data-stu-id="832c8-143">List all of the discovered tests in the current project.</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="832c8-144">Ustawia poziom szczegółowości polecenia.</span><span class="sxs-lookup"><span data-stu-id="832c8-144">Sets the verbosity level of the command.</span></span> <span data-ttu-id="832c8-145">Dozwolone wartości to `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, i `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="832c8-145">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="832c8-146">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="832c8-146">.NET Core 2.0</span></span>](#tab/netcore20)

`-a|--test-adapter-path <PATH_TO_ADAPTER>`

<span data-ttu-id="832c8-147">Używa niestandardowych adapterów testowych z określonej ścieżki w uruchomieniu testu.</span><span class="sxs-lookup"><span data-stu-id="832c8-147">Use the custom test adapters from the specified path in the test run.</span></span>

`-c|--configuration {Debug|Release}`

<span data-ttu-id="832c8-148">Definiuje konfigurację kompilacji.</span><span class="sxs-lookup"><span data-stu-id="832c8-148">Defines the build configuration.</span></span> <span data-ttu-id="832c8-149">Wartość domyślna to `Debug`, ale konfiguracja projektu można zastąpić to ustawienie domyślne zestawu SDK.</span><span class="sxs-lookup"><span data-stu-id="832c8-149">The default value is `Debug`, but your project's configuration could override this default SDK setting.</span></span>

`--collect <DATA_COLLECTOR_FRIENDLY_NAME>`

<span data-ttu-id="832c8-150">Włącza moduł zbierający dane dla uruchomienia testu.</span><span class="sxs-lookup"><span data-stu-id="832c8-150">Enables data collector for the test run.</span></span> <span data-ttu-id="832c8-151">Aby uzyskać więcej informacji, zobacz [monitora i analizować uruchomienia testu](https://aka.ms/vstest-collect).</span><span class="sxs-lookup"><span data-stu-id="832c8-151">For more information, see [Monitor and analyze test run](https://aka.ms/vstest-collect).</span></span>

`-d|--diag <PATH_TO_DIAGNOSTICS_FILE>`

<span data-ttu-id="832c8-152">Włącza tryb diagnostycznych dla testu platformy i zapisu komunikaty diagnostyczne do określonego pliku.</span><span class="sxs-lookup"><span data-stu-id="832c8-152">Enables diagnostic mode for the test platform and write diagnostic messages to the specified file.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="832c8-153">Wyszukuje pliki binarne testów dla określonego [framework](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="832c8-153">Looks for test binaries for a specific [framework](../../standard/frameworks.md).</span></span>

`--filter <EXPRESSION>`

<span data-ttu-id="832c8-154">Odfiltrowuje testy w bieżącym projekcie przy użyciu danego wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="832c8-154">Filters out tests in the current project using the given expression.</span></span> <span data-ttu-id="832c8-155">Aby uzyskać więcej informacji, zobacz [opcję Szczegóły filtru](#filter-option-details) sekcji.</span><span class="sxs-lookup"><span data-stu-id="832c8-155">For more information, see the [Filter option details](#filter-option-details) section.</span></span> <span data-ttu-id="832c8-156">Aby uzyskać dodatkowe informacje i przykłady dotyczące sposobu używania filtrowanie testów jednostki selektywnego, zobacz [przeprowadzanie testów jednostkowych selektywne](../testing/selective-unit-tests.md).</span><span class="sxs-lookup"><span data-stu-id="832c8-156">For more information and examples on how to use selective unit test filtering, see [Running selective unit tests](../testing/selective-unit-tests.md).</span></span>

`-h|--help`

<span data-ttu-id="832c8-157">Drukuje krótkich pomocy dla polecenia.</span><span class="sxs-lookup"><span data-stu-id="832c8-157">Prints out a short help for the command.</span></span>

`-l|--logger <LoggerUri/FriendlyName>`

<span data-ttu-id="832c8-158">Określa Rejestrator dla wyników testu.</span><span class="sxs-lookup"><span data-stu-id="832c8-158">Specifies a logger for test results.</span></span>

`--no-build`

<span data-ttu-id="832c8-159">Nie można utworzyć projektu testowego przed jego uruchomieniem.</span><span class="sxs-lookup"><span data-stu-id="832c8-159">Doesn't build the test project before running it.</span></span> <span data-ttu-id="832c8-160">Niejawne także ustawia `--no-restore` flagi.</span><span class="sxs-lookup"><span data-stu-id="832c8-160">It also implicit sets the `--no-restore` flag.</span></span>

`--no-restore`

<span data-ttu-id="832c8-161">Podczas uruchamiania polecenia przywracania niejawne nie jest wykonywana.</span><span class="sxs-lookup"><span data-stu-id="832c8-161">Doesn't execute an implicit restore when running the command.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="832c8-162">Katalog, w którym można znaleźć plików binarnych do uruchomienia.</span><span class="sxs-lookup"><span data-stu-id="832c8-162">Directory in which to find the binaries to run.</span></span>

`-r|--results-directory <PATH>`

<span data-ttu-id="832c8-163">Katalog, w której będzie można umieścić wyników testu.</span><span class="sxs-lookup"><span data-stu-id="832c8-163">The directory where the test results are going to be placed.</span></span> <span data-ttu-id="832c8-164">Jeśli określony katalog nie istnieje, jest tworzony.</span><span class="sxs-lookup"><span data-stu-id="832c8-164">If the specified directory doesn't exist, it's created.</span></span>

`-s|--settings <SETTINGS_FILE>`

<span data-ttu-id="832c8-165">Ustawienia używane podczas uruchamiania testów.</span><span class="sxs-lookup"><span data-stu-id="832c8-165">Settings to use when running tests.</span></span>

`-t|--list-tests`

<span data-ttu-id="832c8-166">Lista wszystkich odnalezionych testów w bieżącym projekcie.</span><span class="sxs-lookup"><span data-stu-id="832c8-166">List all of the discovered tests in the current project.</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="832c8-167">Ustawia poziom szczegółowości polecenia.</span><span class="sxs-lookup"><span data-stu-id="832c8-167">Sets the verbosity level of the command.</span></span> <span data-ttu-id="832c8-168">Dozwolone wartości to `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, i `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="832c8-168">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="832c8-169">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="832c8-169">.NET Core 1.x</span></span>](#tab/netcore1x)

`-a|--test-adapter-path <PATH_TO_ADAPTER>`

<span data-ttu-id="832c8-170">Używa niestandardowych adapterów testowych z określonej ścieżki w uruchomieniu testu.</span><span class="sxs-lookup"><span data-stu-id="832c8-170">Use the custom test adapters from the specified path in the test run.</span></span>

`-c|--configuration {Debug|Release}`

<span data-ttu-id="832c8-171">Definiuje konfigurację kompilacji.</span><span class="sxs-lookup"><span data-stu-id="832c8-171">Defines the build configuration.</span></span> <span data-ttu-id="832c8-172">Wartość domyślna to `Debug`, ale konfiguracja projektu można zastąpić to ustawienie domyślne zestawu SDK.</span><span class="sxs-lookup"><span data-stu-id="832c8-172">The default value is `Debug`, but your project's configuration could override this default SDK setting.</span></span>

`-d|--diag <PATH_TO_DIAGNOSTICS_FILE>`

<span data-ttu-id="832c8-173">Włącza tryb diagnostycznych dla testu platformy i zapisu komunikaty diagnostyczne do określonego pliku.</span><span class="sxs-lookup"><span data-stu-id="832c8-173">Enables diagnostic mode for the test platform and write diagnostic messages to the specified file.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="832c8-174">Wyszukuje pliki binarne testów dla określonego [framework](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="832c8-174">Looks for test binaries for a specific [framework](../../standard/frameworks.md).</span></span>

`--filter <EXPRESSION>`

<span data-ttu-id="832c8-175">Odfiltrowuje testy w bieżącym projekcie przy użyciu danego wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="832c8-175">Filters out tests in the current project using the given expression.</span></span> <span data-ttu-id="832c8-176">Aby uzyskać więcej informacji, zobacz [opcję Szczegóły filtru](#filter-option-details) sekcji.</span><span class="sxs-lookup"><span data-stu-id="832c8-176">For more information, see the [Filter option details](#filter-option-details) section.</span></span> <span data-ttu-id="832c8-177">Aby uzyskać dodatkowe informacje i przykłady dotyczące sposobu używania filtrowanie testów jednostki selektywnego, zobacz [przeprowadzanie testów jednostkowych selektywne](../testing/selective-unit-tests.md).</span><span class="sxs-lookup"><span data-stu-id="832c8-177">For more information and examples on how to use selective unit test filtering, see [Running selective unit tests](../testing/selective-unit-tests.md).</span></span>

`-h|--help`

<span data-ttu-id="832c8-178">Drukuje krótkich pomocy dla polecenia.</span><span class="sxs-lookup"><span data-stu-id="832c8-178">Prints out a short help for the command.</span></span>

`-l|--logger <LoggerUri/FriendlyName>`

<span data-ttu-id="832c8-179">Określa Rejestrator dla wyników testu.</span><span class="sxs-lookup"><span data-stu-id="832c8-179">Specifies a logger for test results.</span></span>

`--no-build`

<span data-ttu-id="832c8-180">Nie można utworzyć projektu testowego przed jego uruchomieniem.</span><span class="sxs-lookup"><span data-stu-id="832c8-180">Doesn't build the test project before running it.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="832c8-181">Katalog, w którym można znaleźć plików binarnych do uruchomienia.</span><span class="sxs-lookup"><span data-stu-id="832c8-181">Directory in which to find the binaries to run.</span></span>

`-s|--settings <SETTINGS_FILE>`

<span data-ttu-id="832c8-182">Ustawienia używane podczas uruchamiania testów.</span><span class="sxs-lookup"><span data-stu-id="832c8-182">Settings to use when running tests.</span></span>

`-t|--list-tests`

<span data-ttu-id="832c8-183">Lista wszystkich odnalezionych testów w bieżącym projekcie.</span><span class="sxs-lookup"><span data-stu-id="832c8-183">List all of the discovered tests in the current project.</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="832c8-184">Ustawia poziom szczegółowości polecenia.</span><span class="sxs-lookup"><span data-stu-id="832c8-184">Sets the verbosity level of the command.</span></span> <span data-ttu-id="832c8-185">Dozwolone wartości to `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, i `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="832c8-185">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

---

## <a name="examples"></a><span data-ttu-id="832c8-186">Przykłady</span><span class="sxs-lookup"><span data-stu-id="832c8-186">Examples</span></span>

<span data-ttu-id="832c8-187">Uruchom testy w projekcie w bieżącym katalogu:</span><span class="sxs-lookup"><span data-stu-id="832c8-187">Run the tests in the project in the current directory:</span></span>

`dotnet test`

<span data-ttu-id="832c8-188">Uruchom testy `test1` projektu:</span><span class="sxs-lookup"><span data-stu-id="832c8-188">Run the tests in the `test1` project:</span></span>

`dotnet test ~/projects/test1/test1.csproj`

## <a name="filter-option-details"></a><span data-ttu-id="832c8-189">Szczegóły opcji filtru</span><span class="sxs-lookup"><span data-stu-id="832c8-189">Filter option details</span></span>

`--filter <EXPRESSION>`

<span data-ttu-id="832c8-190">`<Expression>` ma format `<property><operator><value>[|&<Expression>]`.</span><span class="sxs-lookup"><span data-stu-id="832c8-190">`<Expression>` has the format `<property><operator><value>[|&<Expression>]`.</span></span>

<span data-ttu-id="832c8-191">`<property>` atrybut `Test Case`.</span><span class="sxs-lookup"><span data-stu-id="832c8-191">`<property>` is an attribute of the `Test Case`.</span></span> <span data-ttu-id="832c8-192">Właściwości obsługiwanych przez platform testów jednostkowych popularnych są następujące:</span><span class="sxs-lookup"><span data-stu-id="832c8-192">The following are the properties supported by popular unit test frameworks:</span></span>

| <span data-ttu-id="832c8-193">Struktury testowej</span><span class="sxs-lookup"><span data-stu-id="832c8-193">Test Framework</span></span> | <span data-ttu-id="832c8-194">Obsługiwanych właściwości</span><span class="sxs-lookup"><span data-stu-id="832c8-194">Supported properties</span></span>                                                                                      |
| -------------- | --------------------------------------------------------------------------------------------------------- |
| <span data-ttu-id="832c8-195">MSTest</span><span class="sxs-lookup"><span data-stu-id="832c8-195">MSTest</span></span>         | <ul><li><span data-ttu-id="832c8-196">FullyQualifiedName</span><span class="sxs-lookup"><span data-stu-id="832c8-196">FullyQualifiedName</span></span></li><li><span data-ttu-id="832c8-197">Nazwa</span><span class="sxs-lookup"><span data-stu-id="832c8-197">Name</span></span></li><li><span data-ttu-id="832c8-198">className</span><span class="sxs-lookup"><span data-stu-id="832c8-198">ClassName</span></span></li><li><span data-ttu-id="832c8-199">Priorytet</span><span class="sxs-lookup"><span data-stu-id="832c8-199">Priority</span></span></li><li><span data-ttu-id="832c8-200">TestCategory</span><span class="sxs-lookup"><span data-stu-id="832c8-200">TestCategory</span></span></li></ul> |
| <span data-ttu-id="832c8-201">xUnit</span><span class="sxs-lookup"><span data-stu-id="832c8-201">xUnit</span></span>          | <ul><li><span data-ttu-id="832c8-202">FullyQualifiedName</span><span class="sxs-lookup"><span data-stu-id="832c8-202">FullyQualifiedName</span></span></li><li><span data-ttu-id="832c8-203">Nazwa wyświetlana</span><span class="sxs-lookup"><span data-stu-id="832c8-203">DisplayName</span></span></li><li><span data-ttu-id="832c8-204">Cechy</span><span class="sxs-lookup"><span data-stu-id="832c8-204">Traits</span></span></li></ul>                                   |

<span data-ttu-id="832c8-205">`<operator>` Opisuje relację między właściwości i wartość:</span><span class="sxs-lookup"><span data-stu-id="832c8-205">The `<operator>` describes the relationship between the property and the value:</span></span>

| <span data-ttu-id="832c8-206">Operator</span><span class="sxs-lookup"><span data-stu-id="832c8-206">Operator</span></span> | <span data-ttu-id="832c8-207">Funkcja</span><span class="sxs-lookup"><span data-stu-id="832c8-207">Function</span></span>        |
| :------: | --------------- |
| `=`      | <span data-ttu-id="832c8-208">Dokładnego dopasowania</span><span class="sxs-lookup"><span data-stu-id="832c8-208">Exact match</span></span>     |
| `!=`     | <span data-ttu-id="832c8-209">Nie dokładnego dopasowania</span><span class="sxs-lookup"><span data-stu-id="832c8-209">Not exact match</span></span> |
| `~`      | <span data-ttu-id="832c8-210">Zawiera</span><span class="sxs-lookup"><span data-stu-id="832c8-210">Contains</span></span>        |

<span data-ttu-id="832c8-211">`<value>` jest to ciąg.</span><span class="sxs-lookup"><span data-stu-id="832c8-211">`<value>` is a string.</span></span> <span data-ttu-id="832c8-212">Wszystkie wyszukiwania są bez uwzględniania wielkości liter.</span><span class="sxs-lookup"><span data-stu-id="832c8-212">All the lookups are case insensitive.</span></span>

<span data-ttu-id="832c8-213">Wyrażenia bez `<operator>` jest automatycznie traktowane jako `contains` na `FullyQualifiedName` właściwości (na przykład `dotnet test --filter xyz` jest taka sama jak `dotnet test --filter FullyQualifiedName~xyz`).</span><span class="sxs-lookup"><span data-stu-id="832c8-213">An expression without an `<operator>` is automatically considered as a `contains` on `FullyQualifiedName` property (for example, `dotnet test --filter xyz` is same as `dotnet test --filter FullyQualifiedName~xyz`).</span></span>

<span data-ttu-id="832c8-214">Może być częścią wyrażenia z operatorami warunkowego:</span><span class="sxs-lookup"><span data-stu-id="832c8-214">Expressions can be joined with conditional operators:</span></span>

| <span data-ttu-id="832c8-215">Operator</span><span class="sxs-lookup"><span data-stu-id="832c8-215">Operator</span></span>            | <span data-ttu-id="832c8-216">Funkcja</span><span class="sxs-lookup"><span data-stu-id="832c8-216">Function</span></span> |
| ------------------- | -------- |
| <code>&#124;</code> | <span data-ttu-id="832c8-217">LUB</span><span class="sxs-lookup"><span data-stu-id="832c8-217">OR</span></span>       |
| `&`                 | <span data-ttu-id="832c8-218">AND</span><span class="sxs-lookup"><span data-stu-id="832c8-218">AND</span></span>      |

<span data-ttu-id="832c8-219">Może być częścią wyrażenia w nawiasach przy użyciu operatorów warunkowych (na przykład `(Name~TestMethod1) | (Name~TestMethod2)`).</span><span class="sxs-lookup"><span data-stu-id="832c8-219">You can enclose expressions in parenthesis when using conditional operators (for example, `(Name~TestMethod1) | (Name~TestMethod2)`).</span></span>

<span data-ttu-id="832c8-220">Aby uzyskać dodatkowe informacje i przykłady dotyczące sposobu używania filtrowanie testów jednostki selektywnego, zobacz [przeprowadzanie testów jednostkowych selektywne](../testing/selective-unit-tests.md).</span><span class="sxs-lookup"><span data-stu-id="832c8-220">For more information and examples on how to use selective unit test filtering, see [Running selective unit tests](../testing/selective-unit-tests.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="832c8-221">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="832c8-221">See also</span></span>

[<span data-ttu-id="832c8-222">Struktury i cele</span><span class="sxs-lookup"><span data-stu-id="832c8-222">Frameworks and Targets</span></span>](../../standard/frameworks.md)  
[<span data-ttu-id="832c8-223">Katalogu .NET core środowiska uruchomieniowego identyfikator (RID)</span><span class="sxs-lookup"><span data-stu-id="832c8-223">.NET Core Runtime IDentifier (RID) catalog</span></span>](../rid-catalog.md)
