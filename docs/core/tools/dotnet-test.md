---
title: polecenie testu dotnet
description: Polecenie testu dotnet służy do wykonywania testów jednostkowych w danym projekcie.
ms.date: 02/27/2020
ms.openlocfilehash: 69b8101f9b1052f4726dce8a86234da99f5dc89c
ms.sourcegitcommit: 73aa9653547a1cd70ee6586221f79cc29b588ebd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2020
ms.locfileid: "82102749"
---
# <a name="dotnet-test"></a><span data-ttu-id="c3c68-103">dotnet test</span><span class="sxs-lookup"><span data-stu-id="c3c68-103">dotnet test</span></span>

<span data-ttu-id="c3c68-104">**Ten artykuł dotyczy:** ✔️.NET Core 2.1 SDK i nowszych wersjach</span><span class="sxs-lookup"><span data-stu-id="c3c68-104">**This article applies to:** ✔️ .NET Core 2.1 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="c3c68-105">Nazwa</span><span class="sxs-lookup"><span data-stu-id="c3c68-105">Name</span></span>

<span data-ttu-id="c3c68-106">`dotnet test`- Sterownik testowy .NET używany do wykonywania testów jednostkowych.</span><span class="sxs-lookup"><span data-stu-id="c3c68-106">`dotnet test` - .NET test driver used to execute unit tests.</span></span>

## <a name="synopsis"></a><span data-ttu-id="c3c68-107">Streszczenie</span><span class="sxs-lookup"><span data-stu-id="c3c68-107">Synopsis</span></span>

```dotnetcli
dotnet test [<PROJECT> | <SOLUTION>]
    [-a|--test-adapter-path <PATH_TO_ADAPTER>] [--blame]
    [-c|--configuration <CONFIGURATION>]
    [--collect <DATA_COLLECTOR_FRIENDLY_NAME>]
    [-d|--diag <PATH_TO_DIAGNOSTICS_FILE>] [-f|--framework <FRAMEWORK>]
    [--filter <EXPRESSION>] [--interactive]
    [-l|--logger <LOGGER_URI/FRIENDLY_NAME>] [--no-build]
    [--nologo] [--no-restore] [-o|--output <OUTPUT_DIRECTORY>]
    [-r|--results-directory <PATH>] [--runtime <RUNTIME_IDENTIFIER>]
    [-s|--settings <SETTINGS_FILE>] [-t|--list-tests]
    [-v|--verbosity <LEVEL>] [[--] <RunSettings arguments>]

dotnet test -h|--help
```

## <a name="description"></a><span data-ttu-id="c3c68-108">Opis</span><span class="sxs-lookup"><span data-stu-id="c3c68-108">Description</span></span>

<span data-ttu-id="c3c68-109">Polecenie `dotnet test` jest używane do wykonywania testów jednostkowych w danym projekcie.</span><span class="sxs-lookup"><span data-stu-id="c3c68-109">The `dotnet test` command is used to execute unit tests in a given project.</span></span> <span data-ttu-id="c3c68-110">Polecenie `dotnet test` uruchamia aplikację konsoli testowej aplikacji dla programu runner określoną dla projektu.</span><span class="sxs-lookup"><span data-stu-id="c3c68-110">The `dotnet test` command launches the test runner console application specified for a project.</span></span> <span data-ttu-id="c3c68-111">Test runner wykonuje testy zdefiniowane dla struktury testów jednostkowych (na przykład MSTest, NUnit lub xUnit) i raportuje sukces lub niepowodzenie każdego testu.</span><span class="sxs-lookup"><span data-stu-id="c3c68-111">The test runner executes the tests defined for a unit test framework (for example, MSTest, NUnit, or xUnit) and reports the success or failure of each test.</span></span> <span data-ttu-id="c3c68-112">Jeśli wszystkie testy zakończą się pomyślnie, test runner zwraca 0 jako kod zakończenia; w przeciwnym razie, jeśli dowolny test zakończy się niepowodzeniem, zwraca wartość 1.</span><span class="sxs-lookup"><span data-stu-id="c3c68-112">If all tests are successful, the test runner returns 0 as an exit code; otherwise if any test fails, it returns 1.</span></span> <span data-ttu-id="c3c68-113">Program testowy i biblioteka testów jednostkowych są pakowane jako pakiety NuGet i są przywracane jako zwykłe zależności dla projektu.</span><span class="sxs-lookup"><span data-stu-id="c3c68-113">The test runner and the unit test library are packaged as NuGet packages and are restored as ordinary dependencies for the project.</span></span>

<span data-ttu-id="c3c68-114">Projekty testowe określają wynik `<PackageReference>` testu przy użyciu zwykłego elementu, jak widać w poniższym przykładowym pliku projektu:</span><span class="sxs-lookup"><span data-stu-id="c3c68-114">Test projects specify the test runner using an ordinary `<PackageReference>` element, as seen in the following sample project file:</span></span>

[!code-xml[XUnit Basic Template](../../../samples/snippets/csharp/xunit-test/xunit-test.csproj)]

### <a name="implicit-restore"></a><span data-ttu-id="c3c68-115">Niejawne przywracanie</span><span class="sxs-lookup"><span data-stu-id="c3c68-115">Implicit restore</span></span>

[!INCLUDE[dotnet restore note](~/includes/dotnet-restore-note.md)]

## <a name="arguments"></a><span data-ttu-id="c3c68-116">Argumenty</span><span class="sxs-lookup"><span data-stu-id="c3c68-116">Arguments</span></span>

- **`PROJECT | SOLUTION`**

  <span data-ttu-id="c3c68-117">Ścieżka do projektu testowego lub rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="c3c68-117">Path to the test project or solution.</span></span> <span data-ttu-id="c3c68-118">Jeśli nie zostanie określony, domyślnie jest to bieżący katalog.</span><span class="sxs-lookup"><span data-stu-id="c3c68-118">If not specified, it defaults to current directory.</span></span>

## <a name="options"></a><span data-ttu-id="c3c68-119">Opcje</span><span class="sxs-lookup"><span data-stu-id="c3c68-119">Options</span></span>

- **`-a|--test-adapter-path <PATH_TO_ADAPTER>`**

  <span data-ttu-id="c3c68-120">Użyj niestandardowych kart testowych z określonej ścieżki w przebiegu testu.</span><span class="sxs-lookup"><span data-stu-id="c3c68-120">Use the custom test adapters from the specified path in the test run.</span></span>

- **`--blame`**

  <span data-ttu-id="c3c68-121">Uruchamia testy w trybie winy.</span><span class="sxs-lookup"><span data-stu-id="c3c68-121">Runs the tests in blame mode.</span></span> <span data-ttu-id="c3c68-122">Ta opcja jest przydatna w izolowaniu problematycznych testów, które powodują awarię hosta testowego.</span><span class="sxs-lookup"><span data-stu-id="c3c68-122">This option is helpful in isolating problematic tests that cause the test host to crash.</span></span> <span data-ttu-id="c3c68-123">Tworzy plik wyjściowy w bieżącym katalogu jako *Sequence.xml,* który przechwytuje kolejność wykonywania testów przed awarią.</span><span class="sxs-lookup"><span data-stu-id="c3c68-123">It creates an output file in the current directory as *Sequence.xml* that captures the order of tests execution before the crash.</span></span>

- **`-c|--configuration <CONFIGURATION>`**

  <span data-ttu-id="c3c68-124">Definiuje konfigurację kompilacji.</span><span class="sxs-lookup"><span data-stu-id="c3c68-124">Defines the build configuration.</span></span> <span data-ttu-id="c3c68-125">Wartością domyślną jest `Debug`, ale konfiguracja projektu może zastąpić to domyślne ustawienie SDK.</span><span class="sxs-lookup"><span data-stu-id="c3c68-125">The default value is `Debug`, but your project's configuration could override this default SDK setting.</span></span>

- **`--collect <DATA_COLLECTOR_FRIENDLY_NAME>`**

  <span data-ttu-id="c3c68-126">Włącza moduł zbierający dane dla przebiegu testowego.</span><span class="sxs-lookup"><span data-stu-id="c3c68-126">Enables data collector for the test run.</span></span> <span data-ttu-id="c3c68-127">Aby uzyskać więcej informacji, zobacz [Monitorowanie i analizowanie przebiegu testowego](https://aka.ms/vstest-collect).</span><span class="sxs-lookup"><span data-stu-id="c3c68-127">For more information, see [Monitor and analyze test run](https://aka.ms/vstest-collect).</span></span>

- **`-d|--diag <PATH_TO_DIAGNOSTICS_FILE>`**

  <span data-ttu-id="c3c68-128">Włącza tryb diagnostyczny dla platformy testowej i zapisuje komunikaty diagnostyczne do określonego pliku.</span><span class="sxs-lookup"><span data-stu-id="c3c68-128">Enables diagnostic mode for the test platform and writes diagnostic messages to the specified file.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="c3c68-129">Wyszukuje pliki binarne testów dla określonej [struktury](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="c3c68-129">Looks for test binaries for a specific [framework](../../standard/frameworks.md).</span></span>

- **`--filter <EXPRESSION>`**

  <span data-ttu-id="c3c68-130">Odfiltrowywają testy w bieżącym projekcie przy użyciu danego wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="c3c68-130">Filters out tests in the current project using the given expression.</span></span> <span data-ttu-id="c3c68-131">Aby uzyskać więcej informacji, zobacz sekcję [Szczegóły opcji filtru.](#filter-option-details)</span><span class="sxs-lookup"><span data-stu-id="c3c68-131">For more information, see the [Filter option details](#filter-option-details) section.</span></span> <span data-ttu-id="c3c68-132">Aby uzyskać więcej informacji i przykładów dotyczących używania selektywnego filtrowania jednostek, zobacz [Uruchamianie testów jednostkowych selektywnych](../testing/selective-unit-tests.md).</span><span class="sxs-lookup"><span data-stu-id="c3c68-132">For more information and examples on how to use selective unit test filtering, see [Running selective unit tests](../testing/selective-unit-tests.md).</span></span>

- **`-h|--help`**

  <span data-ttu-id="c3c68-133">Drukuje krótką pomoc dla polecenia.</span><span class="sxs-lookup"><span data-stu-id="c3c68-133">Prints out a short help for the command.</span></span>

- **`--interactive`**

  <span data-ttu-id="c3c68-134">Umożliwia zatrzymywania polecenia i oczekiwania na dane wejściowe lub akcję użytkownika.</span><span class="sxs-lookup"><span data-stu-id="c3c68-134">Allows the command to stop and wait for user input or action.</span></span> <span data-ttu-id="c3c68-135">Na przykład, aby zakończyć uwierzytelnianie.</span><span class="sxs-lookup"><span data-stu-id="c3c68-135">For example, to complete authentication.</span></span> <span data-ttu-id="c3c68-136">Dostępne od .NET Core 3.0 SDK.</span><span class="sxs-lookup"><span data-stu-id="c3c68-136">Available since .NET Core 3.0 SDK.</span></span>

- **`-l|--logger <LOGGER_URI/FRIENDLY_NAME>`**

  <span data-ttu-id="c3c68-137">Określa rejestrator dla wyników testów.</span><span class="sxs-lookup"><span data-stu-id="c3c68-137">Specifies a logger for test results.</span></span> <span data-ttu-id="c3c68-138">W przeciwieństwie do MSBuild, test dotnet nie akceptuje `-l "console;v=d"` skrótów: zamiast używać `-l "console;verbosity=detailed"`.</span><span class="sxs-lookup"><span data-stu-id="c3c68-138">Unlike MSBuild, dotnet test doesn't accept abbreviations: instead of `-l "console;v=d"` use `-l "console;verbosity=detailed"`.</span></span>

- **`--no-build`**

  <span data-ttu-id="c3c68-139">Nie tworzy projektu testowego przed jego uruchomieniem.</span><span class="sxs-lookup"><span data-stu-id="c3c68-139">Doesn't build the test project before running it.</span></span> <span data-ttu-id="c3c68-140">Również niejawnie ustawia `--no-restore` - flaga.</span><span class="sxs-lookup"><span data-stu-id="c3c68-140">It also implicitly sets the - `--no-restore` flag.</span></span>

- **`--nologo`**

  <span data-ttu-id="c3c68-141">Uruchom testy bez wyświetlania banera Microsoft TestPlatform.</span><span class="sxs-lookup"><span data-stu-id="c3c68-141">Run tests without displaying the Microsoft TestPlatform banner.</span></span> <span data-ttu-id="c3c68-142">Dostępne od .NET Core 3.0 SDK.</span><span class="sxs-lookup"><span data-stu-id="c3c68-142">Available since .NET Core 3.0 SDK.</span></span>

- **`--no-restore`**

  <span data-ttu-id="c3c68-143">Nie wykonuje niejawnego przywracania podczas uruchamiania polecenia.</span><span class="sxs-lookup"><span data-stu-id="c3c68-143">Doesn't execute an implicit restore when running the command.</span></span>

- **`-o|--output <OUTPUT_DIRECTORY>`**

  <span data-ttu-id="c3c68-144">Katalog, w którym można znaleźć pliki binarne do uruchomienia.</span><span class="sxs-lookup"><span data-stu-id="c3c68-144">Directory in which to find the binaries to run.</span></span> <span data-ttu-id="c3c68-145">Jeśli nie zostanie określona, domyślną ścieżką jest `./bin/<configuration>/<framework>/`.</span><span class="sxs-lookup"><span data-stu-id="c3c68-145">If not specified, the default path is `./bin/<configuration>/<framework>/`.</span></span>  <span data-ttu-id="c3c68-146">W przypadku projektów z wieloma `TargetFrameworks` strukturami docelowymi (za pośrednictwem właściwości) należy również zdefiniować `--framework` podczas określania tej opcji.</span><span class="sxs-lookup"><span data-stu-id="c3c68-146">For projects with multiple target frameworks (via the `TargetFrameworks` property), you also need to define `--framework` when you specify this option.</span></span>

- **`-r|--results-directory <PATH>`**

  <span data-ttu-id="c3c68-147">Katalog, w którym zostaną umieszczone wyniki testów.</span><span class="sxs-lookup"><span data-stu-id="c3c68-147">The directory where the test results are going to be placed.</span></span> <span data-ttu-id="c3c68-148">Jeśli określony katalog nie istnieje, jest tworzony.</span><span class="sxs-lookup"><span data-stu-id="c3c68-148">If the specified directory doesn't exist, it's created.</span></span> <span data-ttu-id="c3c68-149">Wartość domyślna znajduje `TestResults` się w katalogu zawierającym plik projektu.</span><span class="sxs-lookup"><span data-stu-id="c3c68-149">The default is `TestResults` in the directory that contains the project file.</span></span>

- **`--runtime <RUNTIME_IDENTIFIER>`**

  <span data-ttu-id="c3c68-150">Docelowy czas wykonywania do przetestowania.</span><span class="sxs-lookup"><span data-stu-id="c3c68-150">The target runtime to test for.</span></span>

- **`-s|--settings <SETTINGS_FILE>`**

  <span data-ttu-id="c3c68-151">Plik `.runsettings` do użycia do uruchamiania testów.</span><span class="sxs-lookup"><span data-stu-id="c3c68-151">The `.runsettings` file to use for running the tests.</span></span> [<span data-ttu-id="c3c68-152">Konfigurowanie testów jednostkowych `.runsettings` przy użyciu pliku.</span><span class="sxs-lookup"><span data-stu-id="c3c68-152">Configure unit tests by using a `.runsettings` file.</span></span>](/visualstudio/test/configure-unit-tests-by-using-a-dot-runsettings-file)

- **`-t|--list-tests`**

  <span data-ttu-id="c3c68-153">Wyświetl listę wszystkich odnalezionych testów w bieżącym projekcie.</span><span class="sxs-lookup"><span data-stu-id="c3c68-153">List all of the discovered tests in the current project.</span></span>

- **`-v|--verbosity <LEVEL>`**

  <span data-ttu-id="c3c68-154">Ustawia poziom szczegółowości polecenia.</span><span class="sxs-lookup"><span data-stu-id="c3c68-154">Sets the verbosity level of the command.</span></span> <span data-ttu-id="c3c68-155">Dozwolone wartości `q[uiet]`to `m[inimal]` `n[ormal]`, `d[etailed]`, `diag[nostic]`, i .</span><span class="sxs-lookup"><span data-stu-id="c3c68-155">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="c3c68-156">Wartość domyślna to `minimal`.</span><span class="sxs-lookup"><span data-stu-id="c3c68-156">The default is `minimal`.</span></span> <span data-ttu-id="c3c68-157">Aby uzyskać więcej informacji, zobacz <xref:Microsoft.Build.Framework.LoggerVerbosity>.</span><span class="sxs-lookup"><span data-stu-id="c3c68-157">For more information, see <xref:Microsoft.Build.Framework.LoggerVerbosity>.</span></span>

- <span data-ttu-id="c3c68-158">**`RunSettings`** Argumenty</span><span class="sxs-lookup"><span data-stu-id="c3c68-158">**`RunSettings`** arguments</span></span>

  <span data-ttu-id="c3c68-159">Argumenty są `RunSettings` przekazywane jako konfiguracje dla testu.</span><span class="sxs-lookup"><span data-stu-id="c3c68-159">Arguments are passed as `RunSettings` configurations for the test.</span></span> <span data-ttu-id="c3c68-160">Argumenty są `[name]=[value]` określane jako pary po "-- " (zwróć uwagę na spację po --).</span><span class="sxs-lookup"><span data-stu-id="c3c68-160">Arguments are specified as `[name]=[value]` pairs after "-- " (note the space after --).</span></span> <span data-ttu-id="c3c68-161">Spacja służy do `[name]=[value]` oddzielania wielu par.</span><span class="sxs-lookup"><span data-stu-id="c3c68-161">A space is used to separate multiple `[name]=[value]` pairs.</span></span>

  <span data-ttu-id="c3c68-162">Przykład: `dotnet test -- MSTest.DeploymentEnabled=false MSTest.MapInconclusiveToFailed=True`</span><span class="sxs-lookup"><span data-stu-id="c3c68-162">Example: `dotnet test -- MSTest.DeploymentEnabled=false MSTest.MapInconclusiveToFailed=True`</span></span>

  <span data-ttu-id="c3c68-163">Aby uzyskać więcej informacji, zobacz [Przekazywanie argumentów RunSettings za pośrednictwem wiersza polecenia](https://github.com/Microsoft/vstest-docs/blob/master/docs/RunSettingsArguments.md).</span><span class="sxs-lookup"><span data-stu-id="c3c68-163">For more information, see [Passing RunSettings arguments through command line](https://github.com/Microsoft/vstest-docs/blob/master/docs/RunSettingsArguments.md).</span></span>

## <a name="examples"></a><span data-ttu-id="c3c68-164">Przykłady</span><span class="sxs-lookup"><span data-stu-id="c3c68-164">Examples</span></span>

- <span data-ttu-id="c3c68-165">Uruchom testy w projekcie w bieżącym katalogu:</span><span class="sxs-lookup"><span data-stu-id="c3c68-165">Run the tests in the project in the current directory:</span></span>

  ```dotnetcli
  dotnet test
  ```

- <span data-ttu-id="c3c68-166">Uruchom testy w `test1` projekcie:</span><span class="sxs-lookup"><span data-stu-id="c3c68-166">Run the tests in the `test1` project:</span></span>

  ```dotnetcli
  dotnet test ~/projects/test1/test1.csproj
  ```

- <span data-ttu-id="c3c68-167">Uruchom testy w projekcie w bieżącym katalogu i wygeneruj plik wyników testu w formacie trx:</span><span class="sxs-lookup"><span data-stu-id="c3c68-167">Run the tests in the project in the current directory, and generate a test results file in the trx format:</span></span>

  ```dotnetcli
  dotnet test --logger trx
  ```

- <span data-ttu-id="c3c68-168">Uruchom testy w projekcie w bieżącym katalogu i zaloguj ze szczegółową szczegółowością do konsoli:</span><span class="sxs-lookup"><span data-stu-id="c3c68-168">Run the tests in the project in the current directory, and log with detailed verbosity to the console:</span></span>

  ```dotnetcli
  dotnet test --logger "console;verbosity=detailed"
  ```

## <a name="filter-option-details"></a><span data-ttu-id="c3c68-169">Szczegóły opcji filtrowania</span><span class="sxs-lookup"><span data-stu-id="c3c68-169">Filter option details</span></span>

`--filter <EXPRESSION>`

<span data-ttu-id="c3c68-170">`<Expression>`ma format `<property><operator><value>[|&<Expression>]`.</span><span class="sxs-lookup"><span data-stu-id="c3c68-170">`<Expression>` has the format `<property><operator><value>[|&<Expression>]`.</span></span>

<span data-ttu-id="c3c68-171">`<property>`jest atrybutem `Test Case`.</span><span class="sxs-lookup"><span data-stu-id="c3c68-171">`<property>` is an attribute of the `Test Case`.</span></span> <span data-ttu-id="c3c68-172">Poniżej przedstawiono właściwości obsługiwane przez popularne struktury testów jednostkowych:</span><span class="sxs-lookup"><span data-stu-id="c3c68-172">The following are the properties supported by popular unit test frameworks:</span></span>

| <span data-ttu-id="c3c68-173">Struktura testów</span><span class="sxs-lookup"><span data-stu-id="c3c68-173">Test Framework</span></span> | <span data-ttu-id="c3c68-174">Obsługiwane właściwości</span><span class="sxs-lookup"><span data-stu-id="c3c68-174">Supported properties</span></span>                                                                                      |
| -------------- | --------------------------------------------------------------------------------------------------------- |
| <span data-ttu-id="c3c68-175">MSTest</span><span class="sxs-lookup"><span data-stu-id="c3c68-175">MSTest</span></span>         | <ul><li><span data-ttu-id="c3c68-176">Pełna w pełni zakwalifikowanananana nazwa</span><span class="sxs-lookup"><span data-stu-id="c3c68-176">FullyQualifiedName</span></span></li><li><span data-ttu-id="c3c68-177">Nazwa</span><span class="sxs-lookup"><span data-stu-id="c3c68-177">Name</span></span></li><li><span data-ttu-id="c3c68-178">ClassName</span><span class="sxs-lookup"><span data-stu-id="c3c68-178">ClassName</span></span></li><li><span data-ttu-id="c3c68-179">Priorytet</span><span class="sxs-lookup"><span data-stu-id="c3c68-179">Priority</span></span></li><li><span data-ttu-id="c3c68-180">Kategoria testowa</span><span class="sxs-lookup"><span data-stu-id="c3c68-180">TestCategory</span></span></li></ul> |
| <span data-ttu-id="c3c68-181">Xunit</span><span class="sxs-lookup"><span data-stu-id="c3c68-181">xUnit</span></span>          | <ul><li><span data-ttu-id="c3c68-182">Pełna w pełni zakwalifikowanananana nazwa</span><span class="sxs-lookup"><span data-stu-id="c3c68-182">FullyQualifiedName</span></span></li><li><span data-ttu-id="c3c68-183">DisplayName</span><span class="sxs-lookup"><span data-stu-id="c3c68-183">DisplayName</span></span></li><li><span data-ttu-id="c3c68-184">Cechy</span><span class="sxs-lookup"><span data-stu-id="c3c68-184">Traits</span></span></li></ul>                                   |

<span data-ttu-id="c3c68-185">Opisuje `<operator>` relację między właściwością a wartością:</span><span class="sxs-lookup"><span data-stu-id="c3c68-185">The `<operator>` describes the relationship between the property and the value:</span></span>

| <span data-ttu-id="c3c68-186">Operator</span><span class="sxs-lookup"><span data-stu-id="c3c68-186">Operator</span></span> | <span data-ttu-id="c3c68-187">Funkcja</span><span class="sxs-lookup"><span data-stu-id="c3c68-187">Function</span></span>        |
| :------: | --------------- |
| `=`      | <span data-ttu-id="c3c68-188">Pełna zgodność</span><span class="sxs-lookup"><span data-stu-id="c3c68-188">Exact match</span></span>     |
| `!=`     | <span data-ttu-id="c3c68-189">Nie dokładne dopasowanie</span><span class="sxs-lookup"><span data-stu-id="c3c68-189">Not exact match</span></span> |
| `~`      | <span data-ttu-id="c3c68-190">Contains</span><span class="sxs-lookup"><span data-stu-id="c3c68-190">Contains</span></span>        |
| `!~`     | <span data-ttu-id="c3c68-191">Nie zawiera</span><span class="sxs-lookup"><span data-stu-id="c3c68-191">Not contains</span></span>    |

<span data-ttu-id="c3c68-192">`<value>`jest ciągiem.</span><span class="sxs-lookup"><span data-stu-id="c3c68-192">`<value>` is a string.</span></span> <span data-ttu-id="c3c68-193">Wszystkie wyszukiwania są niewrażliwe na wielkości liter.</span><span class="sxs-lookup"><span data-stu-id="c3c68-193">All the lookups are case insensitive.</span></span>

<span data-ttu-id="c3c68-194">Wyrażenie bez `<operator>` jest automatycznie traktowane `contains` jako `FullyQualifiedName` właściwość na `dotnet test --filter xyz` (na `dotnet test --filter FullyQualifiedName~xyz`przykład jest taka sama jak ).</span><span class="sxs-lookup"><span data-stu-id="c3c68-194">An expression without an `<operator>` is automatically considered as a `contains` on `FullyQualifiedName` property (for example, `dotnet test --filter xyz` is same as `dotnet test --filter FullyQualifiedName~xyz`).</span></span>

<span data-ttu-id="c3c68-195">Wyrażenia można łączyć z operatorami warunkowymi:</span><span class="sxs-lookup"><span data-stu-id="c3c68-195">Expressions can be joined with conditional operators:</span></span>

| <span data-ttu-id="c3c68-196">Operator</span><span class="sxs-lookup"><span data-stu-id="c3c68-196">Operator</span></span>            | <span data-ttu-id="c3c68-197">Funkcja</span><span class="sxs-lookup"><span data-stu-id="c3c68-197">Function</span></span> |
| ------------------- | -------- |
| <code>&#124;</code> | <span data-ttu-id="c3c68-198">LUB</span><span class="sxs-lookup"><span data-stu-id="c3c68-198">OR</span></span>       |
| `&`                 | <span data-ttu-id="c3c68-199">AND</span><span class="sxs-lookup"><span data-stu-id="c3c68-199">AND</span></span>      |

<span data-ttu-id="c3c68-200">Wyrażenia można ująć w nawiasy podczas korzystania z `(Name~TestMethod1) | (Name~TestMethod2)`operatorów warunkowych (na przykład ).</span><span class="sxs-lookup"><span data-stu-id="c3c68-200">You can enclose expressions in parenthesis when using conditional operators (for example, `(Name~TestMethod1) | (Name~TestMethod2)`).</span></span>

<span data-ttu-id="c3c68-201">Aby uzyskać więcej informacji i przykładów dotyczących używania selektywnego filtrowania jednostek, zobacz [Uruchamianie testów jednostkowych selektywnych](../testing/selective-unit-tests.md).</span><span class="sxs-lookup"><span data-stu-id="c3c68-201">For more information and examples on how to use selective unit test filtering, see [Running selective unit tests](../testing/selective-unit-tests.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="c3c68-202">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c3c68-202">See also</span></span>

- [<span data-ttu-id="c3c68-203">Ramy i cele</span><span class="sxs-lookup"><span data-stu-id="c3c68-203">Frameworks and Targets</span></span>](../../standard/frameworks.md)
- [<span data-ttu-id="c3c68-204">Katalog identyfikatora IDentifier (RID) programu .NET Core</span><span class="sxs-lookup"><span data-stu-id="c3c68-204">.NET Core Runtime IDentifier (RID) catalog</span></span>](../rid-catalog.md)
- [<span data-ttu-id="c3c68-205">Przekazywanie argumentów runsettings za pomocą polecenia</span><span class="sxs-lookup"><span data-stu-id="c3c68-205">Passing runsettings arguments through commandline</span></span>](https://github.com/Microsoft/vstest-docs/blob/master/docs/RunSettingsArguments.md)
