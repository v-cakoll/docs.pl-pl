---
title: polecenie testu dotnet
description: Polecenie testu dotnet służy do wykonywania testów jednostkowych w danym projekcie.
ms.date: 02/27/2020
ms.openlocfilehash: bac2f0e613c34bc9f657551a5eac4038207a93ed
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "78847901"
---
# <a name="dotnet-test"></a><span data-ttu-id="715ba-103">dotnet test</span><span class="sxs-lookup"><span data-stu-id="715ba-103">dotnet test</span></span>

<span data-ttu-id="715ba-104">**Ten artykuł dotyczy:** ✔️ .NET Core 2.1 SDK i nowszych wersji</span><span class="sxs-lookup"><span data-stu-id="715ba-104">**This article applies to:** ✔️ .NET Core 2.1 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="715ba-105">Nazwa</span><span class="sxs-lookup"><span data-stu-id="715ba-105">Name</span></span>

<span data-ttu-id="715ba-106">`dotnet test`- Sterownik testowy .NET używany do wykonywania testów jednostkowych.</span><span class="sxs-lookup"><span data-stu-id="715ba-106">`dotnet test` - .NET test driver used to execute unit tests.</span></span>

## <a name="synopsis"></a><span data-ttu-id="715ba-107">Streszczenie</span><span class="sxs-lookup"><span data-stu-id="715ba-107">Synopsis</span></span>

```dotnetcli
dotnet test [<PROJECT> | <SOLUTION>]
    [-a|--test-adapter-path] [--blame] [-c|--configuration]
    [--collect] [-d|--diag] [-f|--framework] [--filter]
    [--interactive] [-l|--logger] [--no-build] [--nologo]
    [--no-restore] [-o|--output] [-r|--results-directory]
    [--runtime] [-s|--settings] [-t|--list-tests]
    [-v|--verbosity] [[--] <RunSettings arguments>]

dotnet test [-h|--help]
```

## <a name="description"></a><span data-ttu-id="715ba-108">Opis</span><span class="sxs-lookup"><span data-stu-id="715ba-108">Description</span></span>

<span data-ttu-id="715ba-109">Polecenie `dotnet test` służy do wykonywania testów jednostkowych w danym projekcie.</span><span class="sxs-lookup"><span data-stu-id="715ba-109">The `dotnet test` command is used to execute unit tests in a given project.</span></span> <span data-ttu-id="715ba-110">Polecenie `dotnet test` uruchamia aplikację konsoli programu testowego określonej dla projektu.</span><span class="sxs-lookup"><span data-stu-id="715ba-110">The `dotnet test` command launches the test runner console application specified for a project.</span></span> <span data-ttu-id="715ba-111">Test runner wykonuje testy zdefiniowane dla struktury testu jednostkowego (na przykład MSTest, NUnit lub xUnit) i zgłasza powodzenie lub niepowodzenie każdego testu.</span><span class="sxs-lookup"><span data-stu-id="715ba-111">The test runner executes the tests defined for a unit test framework (for example, MSTest, NUnit, or xUnit) and reports the success or failure of each test.</span></span> <span data-ttu-id="715ba-112">Jeśli wszystkie testy się powiodą, test runner zwraca 0 jako kod zakończenia; w przeciwnym razie, jeśli jakikolwiek test nie powiedzie się, zwraca 1.</span><span class="sxs-lookup"><span data-stu-id="715ba-112">If all tests are successful, the test runner returns 0 as an exit code; otherwise if any test fails, it returns 1.</span></span> <span data-ttu-id="715ba-113">Narzędzie do testowania i biblioteka testów jednostkowych są pakowane jako pakiety NuGet i są przywracane jako zwykłe zależności dla projektu.</span><span class="sxs-lookup"><span data-stu-id="715ba-113">The test runner and the unit test library are packaged as NuGet packages and are restored as ordinary dependencies for the project.</span></span>

<span data-ttu-id="715ba-114">Projekty testowe określają testrunner `<PackageReference>` przy użyciu zwykłego elementu, jak widać w następującym przykładowym pliku projektu:</span><span class="sxs-lookup"><span data-stu-id="715ba-114">Test projects specify the test runner using an ordinary `<PackageReference>` element, as seen in the following sample project file:</span></span>

[!code-xml[XUnit Basic Template](../../../samples/snippets/csharp/xunit-test/xunit-test.csproj)]

## <a name="arguments"></a><span data-ttu-id="715ba-115">Argumenty</span><span class="sxs-lookup"><span data-stu-id="715ba-115">Arguments</span></span>

- **`PROJECT | SOLUTION`**

  <span data-ttu-id="715ba-116">Ścieżka do projektu testowego lub rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="715ba-116">Path to the test project or solution.</span></span> <span data-ttu-id="715ba-117">Jeśli nie zostanie określony, domyślnie jest to bieżący katalog.</span><span class="sxs-lookup"><span data-stu-id="715ba-117">If not specified, it defaults to current directory.</span></span>

## <a name="options"></a><span data-ttu-id="715ba-118">Opcje</span><span class="sxs-lookup"><span data-stu-id="715ba-118">Options</span></span>

- **`a|--test-adapter-path <PATH_TO_ADAPTER>`**

  <span data-ttu-id="715ba-119">Użyj niestandardowych kart testowych z określonej ścieżki w przebiegu testowym.</span><span class="sxs-lookup"><span data-stu-id="715ba-119">Use the custom test adapters from the specified path in the test run.</span></span>

- **`-blame`**

  <span data-ttu-id="715ba-120">Uruchamia testy w trybie winy.</span><span class="sxs-lookup"><span data-stu-id="715ba-120">Runs the tests in blame mode.</span></span> <span data-ttu-id="715ba-121">Ta opcja jest pomocna w izolowaniu problematycznych testów, które powodują awarię hosta testowego.</span><span class="sxs-lookup"><span data-stu-id="715ba-121">This option is helpful in isolating problematic tests that cause the test host to crash.</span></span> <span data-ttu-id="715ba-122">Tworzy plik wyjściowy w bieżącym katalogu jako *Sequence.xml,* który przechwytuje kolejność wykonywania testów przed awarią.</span><span class="sxs-lookup"><span data-stu-id="715ba-122">It creates an output file in the current directory as *Sequence.xml* that captures the order of tests execution before the crash.</span></span>

- **`c|--configuration <CONFIGURATION>`**

  <span data-ttu-id="715ba-123">Definiuje konfigurację kompilacji.</span><span class="sxs-lookup"><span data-stu-id="715ba-123">Defines the build configuration.</span></span> <span data-ttu-id="715ba-124">Wartością domyślną jest `Debug`, ale konfiguracja projektu może zastąpić to domyślne ustawienie sdk.</span><span class="sxs-lookup"><span data-stu-id="715ba-124">The default value is `Debug`, but your project's configuration could override this default SDK setting.</span></span>

- **`-collect <DATA_COLLECTOR_FRIENDLY_NAME>`**

  <span data-ttu-id="715ba-125">Włącza moduł zbierający dane dla przebiegu testowego.</span><span class="sxs-lookup"><span data-stu-id="715ba-125">Enables data collector for the test run.</span></span> <span data-ttu-id="715ba-126">Aby uzyskać więcej informacji, zobacz [Monitorowanie i analizowanie przebiegu testowego](https://aka.ms/vstest-collect).</span><span class="sxs-lookup"><span data-stu-id="715ba-126">For more information, see [Monitor and analyze test run](https://aka.ms/vstest-collect).</span></span>

- **`d|--diag <PATH_TO_DIAGNOSTICS_FILE>`**

  <span data-ttu-id="715ba-127">Włącza tryb diagnostyczny dla platformy testowej i zapisu komunikatów diagnostycznych do określonego pliku.</span><span class="sxs-lookup"><span data-stu-id="715ba-127">Enables diagnostic mode for the test platform and write diagnostic messages to the specified file.</span></span>

- **`f|--framework <FRAMEWORK>`**

  <span data-ttu-id="715ba-128">Wyszna testowe pliki binarne dla określonej [struktury](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="715ba-128">Looks for test binaries for a specific [framework](../../standard/frameworks.md).</span></span>

- **`--filter <EXPRESSION>`**

  <span data-ttu-id="715ba-129">Odfiltrowuje testy w bieżącym projekcie przy użyciu danego wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="715ba-129">Filters out tests in the current project using the given expression.</span></span> <span data-ttu-id="715ba-130">Aby uzyskać więcej informacji, zobacz sekcję [Szczegóły opcji filtrowania.](#filter-option-details)</span><span class="sxs-lookup"><span data-stu-id="715ba-130">For more information, see the [Filter option details](#filter-option-details) section.</span></span> <span data-ttu-id="715ba-131">Aby uzyskać więcej informacji i przykłady dotyczące używania selektywnego filtrowania testu jednostkowego, zobacz [Uruchamianie testów jednostkowych selektywnych](../testing/selective-unit-tests.md).</span><span class="sxs-lookup"><span data-stu-id="715ba-131">For more information and examples on how to use selective unit test filtering, see [Running selective unit tests](../testing/selective-unit-tests.md).</span></span>

- **`h|--help`**

  <span data-ttu-id="715ba-132">Drukuje krótką pomoc dla polecenia.</span><span class="sxs-lookup"><span data-stu-id="715ba-132">Prints out a short help for the command.</span></span>

- **`--interactive`**

  <span data-ttu-id="715ba-133">Umożliwia zatrzymanie polecenia i oczekiwanie na wejście użytkownika lub akcję.</span><span class="sxs-lookup"><span data-stu-id="715ba-133">Allows the command to stop and wait for user input or action.</span></span> <span data-ttu-id="715ba-134">Na przykład, aby zakończyć uwierzytelnianie.</span><span class="sxs-lookup"><span data-stu-id="715ba-134">For example, to complete authentication.</span></span> <span data-ttu-id="715ba-135">Dostępne od sdk .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="715ba-135">Available since .NET Core 3.0 SDK.</span></span>

- **`l|--logger <LoggerUri/FriendlyName>`**

  <span data-ttu-id="715ba-136">Określa rejestrator dla wyników testów.</span><span class="sxs-lookup"><span data-stu-id="715ba-136">Specifies a logger for test results.</span></span>

- **`--no-build`**

  <span data-ttu-id="715ba-137">Nie tworzy projekt testowy przed uruchomieniem go.</span><span class="sxs-lookup"><span data-stu-id="715ba-137">Doesn't build the test project before running it.</span></span> <span data-ttu-id="715ba-138">To również niejawnie `--no-restore` ustawia - flaga.</span><span class="sxs-lookup"><span data-stu-id="715ba-138">It also implicitly sets the - `--no-restore` flag.</span></span>

- **`--nologo`**

  <span data-ttu-id="715ba-139">Uruchom testy bez wyświetlania banera Microsoft TestPlatform.</span><span class="sxs-lookup"><span data-stu-id="715ba-139">Run tests without displaying the Microsoft TestPlatform banner.</span></span> <span data-ttu-id="715ba-140">Dostępne od sdk .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="715ba-140">Available since .NET Core 3.0 SDK.</span></span>

- **`--no-restore`**

  <span data-ttu-id="715ba-141">Nie wykonuje przywracania niejawnego podczas uruchamiania polecenia.</span><span class="sxs-lookup"><span data-stu-id="715ba-141">Doesn't execute an implicit restore when running the command.</span></span>

- **`-o|--output <OUTPUT_DIRECTORY>`**

  <span data-ttu-id="715ba-142">Katalog, w którym można znaleźć pliki binarne do uruchomienia.</span><span class="sxs-lookup"><span data-stu-id="715ba-142">Directory in which to find the binaries to run.</span></span>

- **`-r|--results-directory <PATH>`**

  <span data-ttu-id="715ba-143">Katalog, w którym zostaną umieszczone wyniki testów.</span><span class="sxs-lookup"><span data-stu-id="715ba-143">The directory where the test results are going to be placed.</span></span> <span data-ttu-id="715ba-144">Jeśli określony katalog nie istnieje, jest tworzony.</span><span class="sxs-lookup"><span data-stu-id="715ba-144">If the specified directory doesn't exist, it's created.</span></span>

- **`--runtime <RUNTIME_IDENTIFIER>`**

  <span data-ttu-id="715ba-145">Docelowy czas uruchomieniowy do testowania.</span><span class="sxs-lookup"><span data-stu-id="715ba-145">The target runtime to test for.</span></span>

- **`-s|--settings <SETTINGS_FILE>`**

  <span data-ttu-id="715ba-146">Plik `.runsettings` do użycia do uruchamiania testów.</span><span class="sxs-lookup"><span data-stu-id="715ba-146">The `.runsettings` file to use for running the tests.</span></span> [<span data-ttu-id="715ba-147">Konfigurowanie testów `.runsettings` jednostkowych przy użyciu pliku.</span><span class="sxs-lookup"><span data-stu-id="715ba-147">Configure unit tests by using a `.runsettings` file.</span></span>](/visualstudio/test/configure-unit-tests-by-using-a-dot-runsettings-file)

- **`-t|--list-tests`**

  <span data-ttu-id="715ba-148">Lista wszystkich odnalezionych testów w bieżącym projekcie.</span><span class="sxs-lookup"><span data-stu-id="715ba-148">List all of the discovered tests in the current project.</span></span>

- **`-v|--verbosity <LEVEL>`**

  <span data-ttu-id="715ba-149">Ustawia poziom szczegółowości polecenia.</span><span class="sxs-lookup"><span data-stu-id="715ba-149">Sets the verbosity level of the command.</span></span> <span data-ttu-id="715ba-150">Dozwolone wartości `q[uiet]` `m[inimal]`to `n[ormal]` `d[etailed]`, `diag[nostic]`, , i .</span><span class="sxs-lookup"><span data-stu-id="715ba-150">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

- <span data-ttu-id="715ba-151">`RunSettings`Argumenty</span><span class="sxs-lookup"><span data-stu-id="715ba-151">`RunSettings` arguments</span></span>

  <span data-ttu-id="715ba-152">Argumenty są `RunSettings` przekazywane jako konfiguracje dla testu.</span><span class="sxs-lookup"><span data-stu-id="715ba-152">Arguments are passed as `RunSettings` configurations for the test.</span></span> <span data-ttu-id="715ba-153">Argumenty są `[name]=[value]` określane jako pary po "-- " (zwróć uwagę na spacja po --).</span><span class="sxs-lookup"><span data-stu-id="715ba-153">Arguments are specified as `[name]=[value]` pairs after "-- " (note the space after --).</span></span> <span data-ttu-id="715ba-154">Spacja służy do `[name]=[value]` oddzielania wielu par.</span><span class="sxs-lookup"><span data-stu-id="715ba-154">A space is used to separate multiple `[name]=[value]` pairs.</span></span>

  <span data-ttu-id="715ba-155">Przykład: `dotnet test -- MSTest.DeploymentEnabled=false MSTest.MapInconclusiveToFailed=True`</span><span class="sxs-lookup"><span data-stu-id="715ba-155">Example: `dotnet test -- MSTest.DeploymentEnabled=false MSTest.MapInconclusiveToFailed=True`</span></span>

  <span data-ttu-id="715ba-156">Aby uzyskać więcej informacji, zobacz [vstest.console.exe: Przekazywanie RunSettings args](https://github.com/Microsoft/vstest-docs/blob/master/docs/RunSettingsArguments.md).</span><span class="sxs-lookup"><span data-stu-id="715ba-156">For more information, see [vstest.console.exe: Passing RunSettings args](https://github.com/Microsoft/vstest-docs/blob/master/docs/RunSettingsArguments.md).</span></span>

## <a name="examples"></a><span data-ttu-id="715ba-157">Przykłady</span><span class="sxs-lookup"><span data-stu-id="715ba-157">Examples</span></span>

- <span data-ttu-id="715ba-158">Uruchom testy w projekcie w bieżącym katalogu:</span><span class="sxs-lookup"><span data-stu-id="715ba-158">Run the tests in the project in the current directory:</span></span>

  ```dotnetcli
  dotnet test
  ```

- <span data-ttu-id="715ba-159">Uruchom testy w `test1` projekcie:</span><span class="sxs-lookup"><span data-stu-id="715ba-159">Run the tests in the `test1` project:</span></span>

  ```dotnetcli
  dotnet test ~/projects/test1/test1.csproj
  ```

- <span data-ttu-id="715ba-160">Uruchom testy w projekcie w bieżącym katalogu i wygeneruj plik wyników testów w formacie trx:</span><span class="sxs-lookup"><span data-stu-id="715ba-160">Run the tests in the project in the current directory and generate a test results file in the trx format:</span></span>

  ```dotnetcli
  dotnet test --logger trx
  ```

## <a name="filter-option-details"></a><span data-ttu-id="715ba-161">Szczegóły opcji filtrowania</span><span class="sxs-lookup"><span data-stu-id="715ba-161">Filter option details</span></span>

`--filter <EXPRESSION>`

<span data-ttu-id="715ba-162">`<Expression>`ma format `<property><operator><value>[|&<Expression>]`.</span><span class="sxs-lookup"><span data-stu-id="715ba-162">`<Expression>` has the format `<property><operator><value>[|&<Expression>]`.</span></span>

<span data-ttu-id="715ba-163">`<property>`jest atrybutem `Test Case`pliku .</span><span class="sxs-lookup"><span data-stu-id="715ba-163">`<property>` is an attribute of the `Test Case`.</span></span> <span data-ttu-id="715ba-164">Poniżej przedstawiono właściwości obsługiwane przez popularne struktury testów jednostkowych:</span><span class="sxs-lookup"><span data-stu-id="715ba-164">The following are the properties supported by popular unit test frameworks:</span></span>

| <span data-ttu-id="715ba-165">Struktura testów</span><span class="sxs-lookup"><span data-stu-id="715ba-165">Test Framework</span></span> | <span data-ttu-id="715ba-166">Obsługiwane właściwości</span><span class="sxs-lookup"><span data-stu-id="715ba-166">Supported properties</span></span>                                                                                      |
| -------------- | --------------------------------------------------------------------------------------------------------- |
| <span data-ttu-id="715ba-167">MSTest</span><span class="sxs-lookup"><span data-stu-id="715ba-167">MSTest</span></span>         | <ul><li><span data-ttu-id="715ba-168">Nazwa w pełni kwalifikowana</span><span class="sxs-lookup"><span data-stu-id="715ba-168">FullyQualifiedName</span></span></li><li><span data-ttu-id="715ba-169">Nazwa</span><span class="sxs-lookup"><span data-stu-id="715ba-169">Name</span></span></li><li><span data-ttu-id="715ba-170">ClassName</span><span class="sxs-lookup"><span data-stu-id="715ba-170">ClassName</span></span></li><li><span data-ttu-id="715ba-171">Priorytet</span><span class="sxs-lookup"><span data-stu-id="715ba-171">Priority</span></span></li><li><span data-ttu-id="715ba-172">Kategoria testowa</span><span class="sxs-lookup"><span data-stu-id="715ba-172">TestCategory</span></span></li></ul> |
| <span data-ttu-id="715ba-173">Xunit</span><span class="sxs-lookup"><span data-stu-id="715ba-173">xUnit</span></span>          | <ul><li><span data-ttu-id="715ba-174">Nazwa w pełni kwalifikowana</span><span class="sxs-lookup"><span data-stu-id="715ba-174">FullyQualifiedName</span></span></li><li><span data-ttu-id="715ba-175">DisplayName</span><span class="sxs-lookup"><span data-stu-id="715ba-175">DisplayName</span></span></li><li><span data-ttu-id="715ba-176">Cechy</span><span class="sxs-lookup"><span data-stu-id="715ba-176">Traits</span></span></li></ul>                                   |

<span data-ttu-id="715ba-177">Opisuje `<operator>` relację między właściwością a wartością:</span><span class="sxs-lookup"><span data-stu-id="715ba-177">The `<operator>` describes the relationship between the property and the value:</span></span>

| <span data-ttu-id="715ba-178">Operator</span><span class="sxs-lookup"><span data-stu-id="715ba-178">Operator</span></span> | <span data-ttu-id="715ba-179">Funkcja</span><span class="sxs-lookup"><span data-stu-id="715ba-179">Function</span></span>        |
| :------: | --------------- |
| `=`      | <span data-ttu-id="715ba-180">Pełna zgodność</span><span class="sxs-lookup"><span data-stu-id="715ba-180">Exact match</span></span>     |
| `!=`     | <span data-ttu-id="715ba-181">Nie dokładne dopasowanie</span><span class="sxs-lookup"><span data-stu-id="715ba-181">Not exact match</span></span> |
| `~`      | <span data-ttu-id="715ba-182">Contains</span><span class="sxs-lookup"><span data-stu-id="715ba-182">Contains</span></span>        |
| `!~`     | <span data-ttu-id="715ba-183">Nie zawiera</span><span class="sxs-lookup"><span data-stu-id="715ba-183">Not contains</span></span>    |

<span data-ttu-id="715ba-184">`<value>`jest ciągiem znaków.</span><span class="sxs-lookup"><span data-stu-id="715ba-184">`<value>` is a string.</span></span> <span data-ttu-id="715ba-185">Wszystkie wyszukiwania są bez uwzględniania wielkości liter.</span><span class="sxs-lookup"><span data-stu-id="715ba-185">All the lookups are case insensitive.</span></span>

<span data-ttu-id="715ba-186">Wyrażenie bez `<operator>` jest automatycznie traktowane `contains` jako `FullyQualifiedName` na właściwość `dotnet test --filter xyz` (na `dotnet test --filter FullyQualifiedName~xyz`przykład jest taka sama jak ).</span><span class="sxs-lookup"><span data-stu-id="715ba-186">An expression without an `<operator>` is automatically considered as a `contains` on `FullyQualifiedName` property (for example, `dotnet test --filter xyz` is same as `dotnet test --filter FullyQualifiedName~xyz`).</span></span>

<span data-ttu-id="715ba-187">Wyrażenia można łączyć z operatorami warunkowymi:</span><span class="sxs-lookup"><span data-stu-id="715ba-187">Expressions can be joined with conditional operators:</span></span>

| <span data-ttu-id="715ba-188">Operator</span><span class="sxs-lookup"><span data-stu-id="715ba-188">Operator</span></span>            | <span data-ttu-id="715ba-189">Funkcja</span><span class="sxs-lookup"><span data-stu-id="715ba-189">Function</span></span> |
| ------------------- | -------- |
| <code>&#124;</code> | <span data-ttu-id="715ba-190">LUB</span><span class="sxs-lookup"><span data-stu-id="715ba-190">OR</span></span>       |
| `&`                 | <span data-ttu-id="715ba-191">AND</span><span class="sxs-lookup"><span data-stu-id="715ba-191">AND</span></span>      |

<span data-ttu-id="715ba-192">Wyrażenia można ująć w nawias y podczas korzystania z `(Name~TestMethod1) | (Name~TestMethod2)`operatorów warunkowych (na przykład).</span><span class="sxs-lookup"><span data-stu-id="715ba-192">You can enclose expressions in parenthesis when using conditional operators (for example, `(Name~TestMethod1) | (Name~TestMethod2)`).</span></span>

<span data-ttu-id="715ba-193">Aby uzyskać więcej informacji i przykłady dotyczące używania selektywnego filtrowania testu jednostkowego, zobacz [Uruchamianie testów jednostkowych selektywnych](../testing/selective-unit-tests.md).</span><span class="sxs-lookup"><span data-stu-id="715ba-193">For more information and examples on how to use selective unit test filtering, see [Running selective unit tests](../testing/selective-unit-tests.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="715ba-194">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="715ba-194">See also</span></span>

- [<span data-ttu-id="715ba-195">Ramy i cele</span><span class="sxs-lookup"><span data-stu-id="715ba-195">Frameworks and Targets</span></span>](../../standard/frameworks.md)
- [<span data-ttu-id="715ba-196">Wykaz identyfikatora środowiska uruchomienionowego programu .NET Core (RID)</span><span class="sxs-lookup"><span data-stu-id="715ba-196">.NET Core Runtime IDentifier (RID) catalog</span></span>](../rid-catalog.md)
